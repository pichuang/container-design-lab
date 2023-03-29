# Container Design Lab

## Scneario A: USER 0

``` bash
$ docker build -t ghcr.io/pichuang/container-design-lab/user-is-zero -f Dockerfile.user-is-zero .
$ docker images
REPOSITORY                                   TAG                               IMAGE ID       CREATED          SIZE
ghcr.io/pichuang/container-design-lab/user-is-zero                latest                            0f5f964f02f4   26 seconds ago   72.8MB

$ docker run -it --rm ghcr.io/pichuang/container-design-lab/user-is-zero
root@4fb94ac4bbbb:/# id
uid=0(root) gid=0(root) groups=0(root)
```

## Scneario B: USER is not exist

``` bash
$ docker build -t ghcr.io/pichuang/container-design-lab/user-non-exist -f Dockerfile.user-non-exist .
$ docker images
REPOSITORY                                   TAG                               IMAGE ID       CREATED         SIZE
ghcr.io/pichuang/container-design-lab/user-non-exist              latest                            7c5ae2fe7546   5 minutes ago   72.8MB

$ docker run -it --rm ghcr.io/pichuang/container-design-lab/user-non-exist
root@46d2039b2f67:/# id
uid=0(root) gid=0(root) groups=0(root)
```

## Scneario C: USER is 1001 at the end

``` bash
$ docker build -t ghcr.io/pichuang/container-design-lab/user-is-1001-at-the-end -f Dockerfile.user-is-1001-at-the-end .
$ docker images
REPOSITORY                                   TAG                               IMAGE ID       CREATED         SIZE
ghcr.io/pichuang/container-design-lab/user-is-1001-at-the-end     latest                            55c08f1d544b   8 minutes ago   72.8MB

$ docker run -it --rm ghcr.io/pichuang/container-design-lab/user-is-1001-at-the-end
I have no name!@1c1f3f440a00:/$ id
uid=1001 gid=0(root) groups=0(root)
```

## Scneario D: USER is 1001 at the start

``` bash
$ docker build -t ghcr.io/pichuang/container-design-lab/user-is-1001-at-the-start -f Dockerfile.user-is-1001-at-the-start .
 => ERROR [3/3] RUN echo "cat /etc/motd" >> ~/.bashrc                                                                 0.3s
------
 > [3/3] RUN echo "cat /etc/motd" >> ~/.bashrc:
#6 0.301 /bin/sh: 1: cannot create //.bashrc: Permission denied
------
executor failed running [/bin/sh -c echo "cat /etc/motd" >> ~/.bashrc]: exit code: 2
```
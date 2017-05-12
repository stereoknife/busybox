[hub]: https://hub.docker.com/AdamAnt/busybox
[musl]: https://www.musl-libc.org/
[uclibc]: https://www.uclibc.org/

# [adamant/busybox][hub] - A tiny image, nurtured from source

This Docker base image has been custom crafted from source to provide just enough functionality in the tiniest footprint. Included in the image are the following:
 - GNU libc6 (glibc) - _C standard library, found in most linux distributions_ | https://www.gnu.org/software/libc/
 - Busybox - _The Swiss army-knife of linux with hundreds of common utilities_ | https://busybox.net/about.html
 - LibreSSL - _An OpenSSL fork aiming to modernise code and improve security_ | https://www.libressl.org/

Additionally, the following small utilities have been included for convenience and good container practice:
 - su-exec - _A convenient utility for changing user and dropping privilege_ | https://github.com/ncopa/su-exec
 - tini - _A tiny but valid `init` for containers_ | https://github.com/krallin/tini

## Goals for a base image

Occasionally there are opportunities where alternative standard libc implementations ([musl][musl]/[uclibc][uclibc]) won't do, like in the case of [proprietary](http://i.imgur.com/V5K7N1I.jpg) software like [Plex Media Server](https://www.plex.tv/downloads/) where only pre-compiled binaries are provided which were built against the common glibc library.

(_If your use-case doesn't require glibc and you can compile the program from source, we strongly recommend you use the [Alpine Linux](https://hub.docker.com/\_/alpine) image, based on musl, which is smaller and features a full packaging system_)

- The image had to be _small_, whilst still being fully functional
- It should contain a full GNU glibc implementation to support pre-compiled binaries
- There should be enough common system tools available, either GNU coreutils or busybox
- Optionally a pre-installed SSL library as many applications require it
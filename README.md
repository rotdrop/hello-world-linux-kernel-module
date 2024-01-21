# Linux "Hello World!" Kernel Module

Yet another one ...

## References

- C-source code from [mak-/SimplestLKM](https://github.com/maK-/SimplestLKM.git)
- Makefile from [hannesha/it87](https://github.com/hannesha/it87.git). The [Makefile](./Makefile) should be reusable by other kernel modules by simply changing `hello` in

``` makefile
DRIVER = hello
```
to another name. The Makefile expects that the kernel module consists of a singloe source file without headers (i.e. the Makefile does not contain any target dependencies on header files).

## Build

- in order to build for the current kernel version:
``` shell
make clean all install
```
Of course, you can invoke the targets separately. If you are not familiar with `make`, then the suggestion is that you make yourself familiar with it.
- in order to build for another kernel version:
``` shell
make TARGET=X.Y.Z clean all install
```
where `X.Y.Z` is the desired kernel version. For this to work it is necessary that `/lib/modules/X.Y.Z/` exists and contains the installed kernel modules and symlinks to the configured kernel source.

## Usage
Use `insmod` as mentioned in [mak-/SimplestLKM](https://github.com/maK-/SimplestLKM.git/README.md), or after installing issue
``` shell
modprobe hello
```
As mentioned in [mak-/SimplestLKM](https://github.com/maK-/SimplestLKM.git/README.md) you should then have a look at the kernel messages (use e.g. `sudo dmesg` or `sudo journalctl -t kernel` on `systemd` systems or otherwise look at the log-files, it depends on your setup).




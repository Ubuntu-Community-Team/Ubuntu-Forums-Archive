---
title: "LTIB failure in Ubuntu 10.04"
date: 2010-11-21
forum: Desktop Environments
---

### Post by suryaemlinux on 2010-11-21
Hi,
I'm trying to run LTIB on my _Ubuntu_ 10.04. It's failing when it's creating u-boot-mpclite5200b.It's shown below. Any help is really appreciated.
 
 [B][I]
powerpc-603e-linux-gcc -M -g -O2 -fPIC -ffixed-r14 -meabi -D__KERNEL__  -DTEXT_BASE= -I/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include  -fno-builtin -ffreestanding -nostdinc -isystem  /opt/mtwk/usr/local/powerpc-603e-linux/gcc-3.3.2-glibc-2.3.2/lib/gcc-lib/powerpc-603e-linux/3.3.2/include  -pipe -DCONFIG_PPC -D__powerpc__ -DCONFIG_MPC5xxx -ffixed-r2  -ffixed-r29 -mstring -mcpu=603e -mmultiple -Wall -Wstrict-prototypes  asm.S cmp.c cmpi.c two.c twox.c three.c threex.c threei.c andi.c srawi.c  rlwnm.c rlwinm.c rlwimi.c store.c load.c cr.c b.c multi.c string.c  complex.c > .depend
In file included from asm.S:23:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from cmp.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from cmpi.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from two.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from twox.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from three.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from threex.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from threei.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from andi.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from srawi.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from rlwnm.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from rlwinm.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from rlwimi.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from store.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from load.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from cr.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from b.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from multi.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from string.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
In file included from /home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/common.h:35,
from complex.c:24:
/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/include/config.h:6:31: configs/lite5200b.h: No such file or directory
make[1]: *** [.depend] Error 1
make[1]: Leaving directory `/home/lalabs/ltib/rpm/BUILD/u-boot-1.1.3/post/cpu'
make: *** [depend] Error 2
error: Bad exit status from /home/lalabs/ltib/tmp/rpm-tmp.32592 (%build)
 
 
RPM build errors:
Bad exit status from /home/lalabs/ltib/tmp/rpm-tmp.32592 (%build)
Failed building u-boot-mpclite5200b
Died at ./ltib line 351.
 
Started: Fri Nov 19 15:07:50 2010
Ended: Fri Nov 19 15:07:58 2010
Elapsed: 8 seconds
 
Build failures : u-boot-mpclite5200b
Abnormal exit : yes[/I][/B]

---


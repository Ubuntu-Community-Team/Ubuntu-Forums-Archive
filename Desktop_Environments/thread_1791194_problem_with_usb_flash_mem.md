---
title: "problem with usb flash mem"
date: 2011-06-26
forum: Desktop Environments
---

### Post by cqc on 2011-06-26
I cannt open flash memory from my desktop. The icon is shown but i cant mount it. I can only open it form media folder, but i dont have any rights. Can anyone help me? I need this very much.
thanks

---

### Post by Toz on 2011-06-26
Linux will mount flash disks read-only if there is a problem the filesystem. Try checking the flash disk for errors. Open a terminal window and type in the following:
```
sudo dosfsck -v /dev/xxx
```
Replace xxx with the actual device name (it'll be something like /dev/sdb1). If you don't know the device name, type the following in the terminal window:```
sudo tail -f /var/log/syslog
``` insert the flash drive and you will see info display in the terminal window to tell you what it is.

If the first dosfsck command finds errors, you can repair them by adding the -a parameter like:```
sudo dosfck -a -v /dev/xxx
```

---

### Post by searchfgold6789 on 2011-06-26
You might not have been granted permission to access any non-/ external media, although I can't think of any reason why this might be changed.
If you are the Administrator, I would check under Users and accounts(?). I know there is a menu there where you can select exactly hich individual user should be able to do.

---

### Post by cqc on 2011-06-26
No thats not it, i tried noting happens. I mean i execute give commands and nothing i still cant access it

---

### Post by Toz on 2011-06-26
Can you post back the commands that you used and the results of those commands?

---

### Post by cqc on 2011-06-30
```
sudo dosfsck -v /dev/xxx
```
```
sudo tail -f /var/log/syslog
```
```
sudo dosfck -a -v /dev/xxx
```
I used this commands and got nothing. I can access usb memory from /media, but i have to use ```
gksudo
``` in oder to gain permission for writing.

---

### Post by Ozymandias_117 on 2011-06-30
Could you please post the output of ```
mount
```

---

### Post by cqc on 2011-06-30
> **Ozymandias_117 said:**
> Could you please post the output of ```
mount
```
here you go
```
/dev/sda1 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/usbhd-sda1 type ext4 (rw,relatime,commit=0,commit=0)
/dev/sdb1 on /media/apacer type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stojakov/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stojakov)

```

---

### Post by Ozymandias_117 on 2011-06-30
Er... Are you RUNNING off the flash drive...? Your root partition is /dev/sda1... and it's also mounted to /media/usbhd-sda1/... And whatever /dev/sdb is (Or is THIS your flash drive...) is mounted with fuse...

Why don't you go ahead and post the output of ```
sudo fdisk -l
``` as well...

---

### Post by cqc on 2011-06-30
[IMG]http://images.ncix.com/forumimages/A98672EC-9EAF-409D-AA87FFED88F86086.jpg[/IMG]
i forgot, sorry. here is mount again
```
/dev/sda1 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /media/usbhd-sda1 type ext4 (rw,relatime,commit=0,commit=0)
/dev/sdb1 on /media/apacer type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/stojakov/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=stojakov)
/dev/sdc1 on /media/disk type vfat (rw,relatime,utf8,gid=100,umask=002)

```flash drive is sdc1
```
&#1044;&#1080;&#1089;&#1082; /dev/sda: 80.1 GB, 80060424192 &#1073;&#1072;&#1112;&#1090;&#1072;
255 &#1075;&#1083;&#1072;&#1074;&#1072;, 63 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;/&#1089;&#1090;&#1072;&#1079;&#1072;, 9733 &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072;
&#1032;&#1077;&#1076;&#1080;&#1085;&#1080;&#1094;&#1077; = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072; &#1086;&#1076; 16065 * 512 = 8225280 &#1073;&#1072;&#1112;&#1090;&#1072;
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x000931cd

&#1059;&#1088;&#1077;&#1106;&#1072;&#1112; &#1041;&#1091;&#1090;      &#1055;&#1086;&#1095;&#1077;&#1090;&#1072;&#1082;         &#1050;&#1088;&#1072;&#1112;      &#1041;&#1083;&#1086;&#1082;&#1086;&#1074;&#1072;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;
/dev/sda1   *           1        9636    77396992   83  Linux
/dev/sda2            9636        9734      784385    5  &#1055;&#1088;&#1086;&#1096;&#1080;&#1088;&#1077;&#1085;&#1086;
/dev/sda5            9636        9734      784384   82  Linux swap / Solaris

&#1044;&#1080;&#1089;&#1082; /dev/sdb: 320.1 GB, 320072931328 &#1073;&#1072;&#1112;&#1090;&#1072;
255 &#1075;&#1083;&#1072;&#1074;&#1072;, 63 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;/&#1089;&#1090;&#1072;&#1079;&#1072;, 38913 &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072;
&#1032;&#1077;&#1076;&#1080;&#1085;&#1080;&#1094;&#1077; = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072; &#1086;&#1076; 16065 * 512 = 8225280 &#1073;&#1072;&#1112;&#1090;&#1072;
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x000affef

&#1059;&#1088;&#1077;&#1106;&#1072;&#1112; &#1041;&#1091;&#1090;      &#1055;&#1086;&#1095;&#1077;&#1090;&#1072;&#1082;         &#1050;&#1088;&#1072;&#1112;      &#1041;&#1083;&#1086;&#1082;&#1086;&#1074;&#1072;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

&#1044;&#1080;&#1089;&#1082; /dev/sdc: 1002 MB, 1002438656 &#1073;&#1072;&#1112;&#1090;&#1072;
31 &#1075;&#1083;&#1072;&#1074;&#1072;, 62 &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;/&#1089;&#1090;&#1072;&#1079;&#1072;, 1018 &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072;
&#1032;&#1077;&#1076;&#1080;&#1085;&#1080;&#1094;&#1077; = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1072;&#1088;&#1072; &#1086;&#1076; 1922 * 512 = 984064 &#1073;&#1072;&#1112;&#1090;&#1072;
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
&#1048;&#1076;&#1077;&#1085;&#1090;&#1080;&#1092;&#1080;&#1082;&#1072;&#1090;&#1086;&#1088; &#1076;&#1080;&#1089;&#1082;&#1072;: 0x0002b949

&#1059;&#1088;&#1077;&#1106;&#1072;&#1112; &#1041;&#1091;&#1090;      &#1055;&#1086;&#1095;&#1077;&#1090;&#1072;&#1082;         &#1050;&#1088;&#1072;&#1112;      &#1041;&#1083;&#1086;&#1082;&#1086;&#1074;&#1072;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;
/dev/sdc1   *           1        1018      978267    c  W95 FAT32 (LBA)

```

---

### Post by Toz on 2011-06-30
What does ```
sudo dosfsck -v /dev/sdc1
``` return?

---

### Post by cqc on 2011-06-30
> **Toz said:**
> What does ```
sudo dosfsck -v /dev/sdc1
``` return?
```
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  3:53/6d, 4:59/6b, 5:53/64, 6:4c/6f, 7:49/73, 8:4e/66, 9:55/73, 10:58/00
  , 90:fa/0e, 91:fc/1f, 92:31/be, 93:c9/77, 94:8e/7c, 95:d1/ac, 96:bc/22
  , 97:76/c0, 98:7b/74, 99:52/0b, 100:06/56, 101:57/b4, 102:8e/0e, 103:c1/bb
  , 104:b1/07, 105:26/00, 106:bf/cd, 107:78/10, 108:7b/5e, 109:f3/eb
  , 110:a5/f0, 111:8e/32, 112:d9/e4, 113:bb/cd, 114:78/16, 115:00/cd
  , 116:0f/19, 117:b4/eb, 118:37/fe, 119:0f/54, 120:a0/68, 121:56/69
  , 122:20/73, 123:d2/20, 124:78/69, 125:1b/73, 126:31/20, 127:c0/6e
  , 128:b1/6f, 129:06/74, 130:89/20, 131:3f/61, 132:89/20, 133:47/62
  , 134:02/6f, 135:f3/6f, 136:64/74, 137:a5/61, 138:8a/62, 139:0e/6c
  , 140:18/65, 141:7c/20, 142:88/64, 143:4d/69, 144:bc/73, 145:50/6b
  , 146:50/2e, 147:50/20, 148:50/20, 149:cd/50, 150:13/6c, 151:eb/65
  , 152:4b/61, 153:f6/73, 154:45/65, 155:b4/20, 156:7f/69, 157:75/6e
  , 158:25/73, 159:38/65, 160:4d/72, 161:b8/74, 162:74/20, 163:20/61
  , 164:66/20, 165:3d/62, 166:21/6f, 167:47/6f, 168:50/74, 169:54/61
  , 170:75/62, 171:10/6c, 172:80/65, 173:7d/20, 174:b8/66, 175:ed/6c
  , 176:75/6f, 177:0a/70, 178:66/70, 179:ff/79, 180:75/20, 181:ec/61
  , 182:66/6e, 183:ff/64, 184:75/0d, 185:e8/0a, 186:eb/70, 187:0f/72
  , 188:51/65, 189:51/73, 190:66/73, 191:ff/20, 192:75/61, 193:bc/6e
  , 194:eb/79, 195:07/20, 196:51/6b, 197:51/65, 198:66/79, 199:ff/20
  , 200:36/74, 201:1c/6f, 202:7c/20, 203:b4/74, 204:08/72, 205:cd/79
  , 206:13/20, 207:72/61, 208:13/67, 209:20/61, 210:e4/69, 211:75/6e
  , 212:0f/20, 213:c1/2e, 214:ea/2e, 215:08/2e, 216:42/20, 217:89/0d
  , 218:16/0a, 219:1a/00, 220:7c/00, 221:83/00, 222:e1/00, 223:3f/00
  , 224:89/00, 225:0e/00, 226:18/00, 227:7c/00, 228:fb/00, 229:bb/00
  , 230:aa/00, 231:55/00, 232:b4/00, 233:41/00, 234:8a/00, 235:16/00
  , 236:74/00, 237:7b/00, 238:cd/00, 239:13/00, 240:72/00, 241:10/00
  , 242:81/00, 243:fb/00, 244:55/00, 245:aa/00, 246:75/00, 247:0a/00
  , 248:f6/00, 249:c1/00, 250:01/00, 251:74/00, 252:05/00, 253:c6/00
  , 254:06/00, 255:32/00, 256:7d/00, 258:66/00, 259:b8/00, 260:8e/00
  , 261:0f/00, 262:16/00, 264:66/00, 265:ba/00, 270:bb/00, 272:7e/00
  , 273:e8/00, 274:10/00, 276:66/00, 277:81/00, 278:3e/00, 279:2c/00
  , 280:7e/00, 281:ce/00, 282:0d/00, 283:08/00, 284:72/00, 285:75/00
  , 286:76/00, 287:ea/00, 288:40/00, 289:7e/00, 292:66/00, 293:03/00
  , 294:06/00, 295:64/00, 296:7b/00, 297:66/00, 298:13/00, 299:16/00
  , 300:68/00, 301:7b/00, 302:b9/00, 303:10/00, 305:eb/00, 306:2b/00
  , 307:66/00, 308:52/00, 309:66/00, 310:50/00, 311:06/00, 312:53/00
  , 313:6a/00, 314:01/00, 315:6a/00, 316:10/00, 317:89/00, 318:e6/00
  , 319:66/00, 320:60/00, 321:b4/00, 322:42/00, 323:e8/00, 324:7f/00
  , 326:66/00, 327:61/00, 328:8d/00, 329:64/00, 330:10/00, 331:72/00
  , 332:01/00, 333:c3/00, 334:66/00, 335:60/00, 336:31/00, 337:c0/00
  , 338:e8/00, 339:70/00, 341:66/00, 342:61/00, 343:e2/00, 344:da/00
  , 345:c6/00, 346:06/00, 347:32/00, 348:7d/00, 349:2b/00, 350:66/00
  , 351:60/00, 352:66/00, 353:0f/00, 354:b7/00, 355:36/00, 356:18/00
  , 357:7c/00, 358:66/00, 359:0f/00, 360:b7/00, 361:3e/00, 362:1a/00
  , 363:7c/00, 364:66/00, 365:f7/00, 366:f6/00, 367:31/00, 368:c9/00
  , 369:87/00, 370:ca/00, 371:66/00, 372:f7/00, 373:f7/00, 374:66/00
  , 375:3d/00, 376:ff/00, 377:03/00, 380:77/00, 381:17/00, 382:c0/00
  , 383:e4/00, 384:06/00, 385:41/00, 386:08/00, 387:e1/00, 388:88/00
  , 389:c5/00, 390:88/00, 391:d6/00, 392:b8/00, 393:01/00, 394:02/00
  , 395:e8/00, 396:37/00, 398:66/00, 399:61/00, 400:72/00, 401:01/00
  , 402:c3/00, 403:e2/00, 404:c9/00, 405:31/00, 406:f6/00, 407:8e/00
  , 408:d6/00, 409:bc/00, 410:6c/00, 411:7b/00, 412:8e/00, 413:de/00
  , 414:66/00, 415:8f/00, 416:06/00, 417:78/00, 419:be/00, 420:cc/00
  , 421:7d/00, 422:e8/00, 423:09/00, 425:31/00, 426:c0/00, 427:cd/00
  , 428:16/00, 429:cd/00, 430:19/00, 431:f4/00, 432:eb/00, 433:fd/00
  , 434:66/00, 435:60/00, 436:ac/00, 437:20/00, 438:c0/00, 439:74/00
  , 440:09/00, 441:b4/00, 442:0e/00, 443:bb/00, 444:07/00, 446:cd/00
  , 447:10/00, 448:eb/00, 449:f2/00, 450:66/00, 451:61/00, 452:c3/00
  , 453:8a/00, 454:16/00, 455:74/00, 456:7b/00, 457:cd/00, 458:13/00
  , 459:c3/00, 460:42/00, 461:6f/00, 462:6f/00, 463:74/00, 464:20/00
  , 465:65/00, 466:72/00, 467:72/00, 468:6f/00, 469:72/00, 470:0d/00
  , 471:0a/00
1) Copy original to backup
2) Copy backup to original
3) No action

```

---

### Post by Toz on 2011-06-30
Backup the data on the flash drive.

This time run:
```
sudo dosfsck -a -v /dev/sdc1
```

If prompted with the 3 choices again, choose choice #1.

IF prompted "Perform changes?" - choose Yes (Y).

---

### Post by cqc on 2011-06-30
> **Toz said:**
> Backup the data on the flash drive.

This time run:
```
sudo dosfsck -a -v /dev/sdc1
```If prompted with the 3 choices again, choose choice #1.

IF prompted "Perform changes?" - choose Yes (Y).
```
dosfsck 3.0.9 (31 Jan 2010)
dosfsck 3.0.9, 31 Jan 2010, FAT32, LFN
Checking we can access the last sector of the filesystem
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  3:53/6d, 4:59/6b, 5:53/64, 6:4c/6f, 7:49/73, 8:4e/66, 9:55/73, 10:58/00
  , 90:fa/0e, 91:fc/1f, 92:31/be, 93:c9/77, 94:8e/7c, 95:d1/ac, 96:bc/22
  , 97:76/c0, 98:7b/74, 99:52/0b, 100:06/56, 101:57/b4, 102:8e/0e, 103:c1/bb
  , 104:b1/07, 105:26/00, 106:bf/cd, 107:78/10, 108:7b/5e, 109:f3/eb
  , 110:a5/f0, 111:8e/32, 112:d9/e4, 113:bb/cd, 114:78/16, 115:00/cd
  , 116:0f/19, 117:b4/eb, 118:37/fe, 119:0f/54, 120:a0/68, 121:56/69
  , 122:20/73, 123:d2/20, 124:78/69, 125:1b/73, 126:31/20, 127:c0/6e
  , 128:b1/6f, 129:06/74, 130:89/20, 131:3f/61, 132:89/20, 133:47/62
  , 134:02/6f, 135:f3/6f, 136:64/74, 137:a5/61, 138:8a/62, 139:0e/6c
  , 140:18/65, 141:7c/20, 142:88/64, 143:4d/69, 144:bc/73, 145:50/6b
  , 146:50/2e, 147:50/20, 148:50/20, 149:cd/50, 150:13/6c, 151:eb/65
  , 152:4b/61, 153:f6/73, 154:45/65, 155:b4/20, 156:7f/69, 157:75/6e
  , 158:25/73, 159:38/65, 160:4d/72, 161:b8/74, 162:74/20, 163:20/61
  , 164:66/20, 165:3d/62, 166:21/6f, 167:47/6f, 168:50/74, 169:54/61
  , 170:75/62, 171:10/6c, 172:80/65, 173:7d/20, 174:b8/66, 175:ed/6c
  , 176:75/6f, 177:0a/70, 178:66/70, 179:ff/79, 180:75/20, 181:ec/61
  , 182:66/6e, 183:ff/64, 184:75/0d, 185:e8/0a, 186:eb/70, 187:0f/72
  , 188:51/65, 189:51/73, 190:66/73, 191:ff/20, 192:75/61, 193:bc/6e
  , 194:eb/79, 195:07/20, 196:51/6b, 197:51/65, 198:66/79, 199:ff/20
  , 200:36/74, 201:1c/6f, 202:7c/20, 203:b4/74, 204:08/72, 205:cd/79
  , 206:13/20, 207:72/61, 208:13/67, 209:20/61, 210:e4/69, 211:75/6e
  , 212:0f/20, 213:c1/2e, 214:ea/2e, 215:08/2e, 216:42/20, 217:89/0d
  , 218:16/0a, 219:1a/00, 220:7c/00, 221:83/00, 222:e1/00, 223:3f/00
  , 224:89/00, 225:0e/00, 226:18/00, 227:7c/00, 228:fb/00, 229:bb/00
  , 230:aa/00, 231:55/00, 232:b4/00, 233:41/00, 234:8a/00, 235:16/00
  , 236:74/00, 237:7b/00, 238:cd/00, 239:13/00, 240:72/00, 241:10/00
  , 242:81/00, 243:fb/00, 244:55/00, 245:aa/00, 246:75/00, 247:0a/00
  , 248:f6/00, 249:c1/00, 250:01/00, 251:74/00, 252:05/00, 253:c6/00
  , 254:06/00, 255:32/00, 256:7d/00, 258:66/00, 259:b8/00, 260:8e/00
  , 261:0f/00, 262:16/00, 264:66/00, 265:ba/00, 270:bb/00, 272:7e/00
  , 273:e8/00, 274:10/00, 276:66/00, 277:81/00, 278:3e/00, 279:2c/00
  , 280:7e/00, 281:ce/00, 282:0d/00, 283:08/00, 284:72/00, 285:75/00
  , 286:76/00, 287:ea/00, 288:40/00, 289:7e/00, 292:66/00, 293:03/00
  , 294:06/00, 295:64/00, 296:7b/00, 297:66/00, 298:13/00, 299:16/00
  , 300:68/00, 301:7b/00, 302:b9/00, 303:10/00, 305:eb/00, 306:2b/00
  , 307:66/00, 308:52/00, 309:66/00, 310:50/00, 311:06/00, 312:53/00
  , 313:6a/00, 314:01/00, 315:6a/00, 316:10/00, 317:89/00, 318:e6/00
  , 319:66/00, 320:60/00, 321:b4/00, 322:42/00, 323:e8/00, 324:7f/00
  , 326:66/00, 327:61/00, 328:8d/00, 329:64/00, 330:10/00, 331:72/00
  , 332:01/00, 333:c3/00, 334:66/00, 335:60/00, 336:31/00, 337:c0/00
  , 338:e8/00, 339:70/00, 341:66/00, 342:61/00, 343:e2/00, 344:da/00
  , 345:c6/00, 346:06/00, 347:32/00, 348:7d/00, 349:2b/00, 350:66/00
  , 351:60/00, 352:66/00, 353:0f/00, 354:b7/00, 355:36/00, 356:18/00
  , 357:7c/00, 358:66/00, 359:0f/00, 360:b7/00, 361:3e/00, 362:1a/00
  , 363:7c/00, 364:66/00, 365:f7/00, 366:f6/00, 367:31/00, 368:c9/00
  , 369:87/00, 370:ca/00, 371:66/00, 372:f7/00, 373:f7/00, 374:66/00
  , 375:3d/00, 376:ff/00, 377:03/00, 380:77/00, 381:17/00, 382:c0/00
  , 383:e4/00, 384:06/00, 385:41/00, 386:08/00, 387:e1/00, 388:88/00
  , 389:c5/00, 390:88/00, 391:d6/00, 392:b8/00, 393:01/00, 394:02/00
  , 395:e8/00, 396:37/00, 398:66/00, 399:61/00, 400:72/00, 401:01/00
  , 402:c3/00, 403:e2/00, 404:c9/00, 405:31/00, 406:f6/00, 407:8e/00
  , 408:d6/00, 409:bc/00, 410:6c/00, 411:7b/00, 412:8e/00, 413:de/00
  , 414:66/00, 415:8f/00, 416:06/00, 417:78/00, 419:be/00, 420:cc/00
  , 421:7d/00, 422:e8/00, 423:09/00, 425:31/00, 426:c0/00, 427:cd/00
  , 428:16/00, 429:cd/00, 430:19/00, 431:f4/00, 432:eb/00, 433:fd/00
  , 434:66/00, 435:60/00, 436:ac/00, 437:20/00, 438:c0/00, 439:74/00
  , 440:09/00, 441:b4/00, 442:0e/00, 443:bb/00, 444:07/00, 446:cd/00
  , 447:10/00, 448:eb/00, 449:f2/00, 450:66/00, 451:61/00, 452:c3/00
  , 453:8a/00, 454:16/00, 455:74/00, 456:7b/00, 457:cd/00, 458:13/00
  , 459:c3/00, 460:42/00, 461:6f/00, 462:6f/00, 463:74/00, 464:20/00
  , 465:65/00, 466:72/00, 467:72/00, 468:6f/00, 469:72/00, 470:0d/00
  , 471:0a/00
  Not automatically fixing this.
Boot sector contents:
System ID "SYSLINUX"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      4096 bytes per cluster
        32 reserved sectors
First FAT starts at byte 16384 (sector 32)
         2 FATs, 32 bit entries
    976384 bytes per FAT (= 1907 sectors)
Root directory start at cluster 2 (arbitrary size)
Data area starts at byte 1969152 (sector 3846)
    244086 data clusters (999776256 bytes)
62 sectors/track, 31 heads
         0 hidden sectors
   1956534 sectors total
Reclaiming unconnected clusters.
Checking free cluster summary.
/dev/sdc1: 280 files, 180249/244086 clusters

```i dont think there is any problem with my flash drive. I tried several different ones i cant access to any of them. I go right click on them and choose mount and nothing happens, no message, no error nothing. Maybe i have problem with mounting drives

---


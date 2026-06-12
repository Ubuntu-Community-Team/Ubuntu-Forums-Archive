---
title: "[SOLVED] Creating .iso from files in folder"
date: 2008-12-05
forum: General Help
---

### Post by detroit/zero on 2008-12-05
Can someone help me create an .iso disk-image from a folder I have?

I'm trying to use the mkisofs command - and it is working - but it's changing all my filenames for some reason and adding extensions where there should be none.

I have a directory with a bunch of subfolders structured: [COLOR=Blue]XXX##_##[/COLOR]where XXX is some letters, and ## is numbers. Obviously, not all letters and numbers are the same. When I run the command, the iso file is created, but all the filenames have been changed.

For example: [COLOR=Blue]XXX##_##[/COLOR] is changed to [COLOR=Blue]xx####xx[/COLOR] in some places, [COLOR=Blue]xx####.txt[/COLOR] in other places, and [COLOR=Blue]xxx####.cxt[/COLOR] in still other places. Keep in mind that all of these, without exception, are folders with various media files inside; none of them are text or .cxt files.

The command I'm using is```
mkisofs -o ISONAME.iso ./*
```I tried checking the help file, but I don't fully understand the options described.

---

### Post by maybeway36 on 2008-12-05
You should add the options "-J" (Joliet - Windows extenstions) and "-r" (Rock Ridge - Unix extensions).

---

### Post by detroit/zero on 2008-12-05
No good. It did change how the files are being renamed, in that now everything is being renamed in ALL CAPS, but all the name changes are the same. Here's a list of the two directories for comparison so you can see what's going on```
zero@zero-laptop:~/Desktop/Polish I$ ls
CATMPC.TRS   PCT03_03  PCT05_08  PCT07_11  POL02_03  POL04_08  POL06_12
CDID.TRS     PCT03_04  PCT05_09  PCT07_12  POL02_04  POL04_09  POL07_01
Credits.TRS  PCT03_05  PCT05_10  PCT08_01  POL02_05  POL04_10  POL07_02
PCT01_01     PCT03_06  PCT05_11  PCT08_02  POL02_06  POL04_11  POL07_03
PCT01_02     PCT03_07  PCT05_12  PCT08_03  POL02_07  POL05_01  POL07_04
PCT01_03     PCT03_08  PCT06_01  PCT08_04  POL02_08  POL05_02  POL07_05
PCT01_04     PCT03_09  PCT06_02  PCT08_05  POL02_09  POL05_03  POL07_06
PCT01_05     PCT03_10  PCT06_03  PCT08_06  POL02_10  POL05_04  POL07_07
PCT01_06     PCT03_11  PCT06_04  PCT08_07  POL02_11  POL05_05  POL07_08
PCT01_07     PCT04_01  PCT06_05  PCT08_08  POL03_01  POL05_06  POL07_09
PCT01_08     PCT04_02  PCT06_06  PCT08_09  POL03_02  POL05_07  POL07_10
PCT01_09     PCT04_03  PCT06_07  PCT08_10  POL03_03  POL05_08  POL07_11
PCT01_10     PCT04_04  PCT06_08  PCT08_11  POL03_04  POL05_09  POL07_12
PCT01_11     PCT04_05  PCT06_09  PCT08_12  POL03_05  POL05_10  POL08_01
PCT02_01     PCT04_06  PCT06_10  POL01_01  POL03_06  POL05_11  POL08_02
PCT02_02     PCT04_07  PCT06_11  POL01_02  POL03_07  POL05_12  POL08_03
PCT02_03     PCT04_08  PCT06_12  POL01_03  POL03_08  POL06_01  POL08_04
PCT02_04     PCT04_09  PCT07_01  POL01_04  POL03_09  POL06_02  POL08_05
PCT02_05     PCT04_10  PCT07_02  POL01_05  POL03_10  POL06_03  POL08_06
PCT02_06     PCT04_11  PCT07_03  POL01_06  POL03_11  POL06_04  POL08_07
PCT02_07     PCT05_01  PCT07_04  POL01_07  POL04_01  POL06_05  POL08_08
PCT02_08     PCT05_02  PCT07_05  POL01_08  POL04_02  POL06_06  POL08_09
PCT02_09     PCT05_03  PCT07_06  POL01_09  POL04_03  POL06_07  POL08_10
PCT02_10     PCT05_04  PCT07_07  POL01_10  POL04_04  POL06_08  POL08_11
PCT02_11     PCT05_05  PCT07_08  POL01_11  POL04_05  POL06_09  POL08_12
PCT03_01     PCT05_06  PCT07_09  POL02_01  POL04_06  POL06_10
PCT03_02     PCT05_07  PCT07_10  POL02_02  POL04_07  POL06_11

```becomes```
zero@zero-laptop:/media/cdrom0$ ls
CATMPC.TRS   PC0604P     PO0204.TXT  PO0502.TXT  PO0709.TXT   POS0310.CXT
CDID.TRS     PC0605P     PO0205S     PO0503S     PO0710S      POS0311.CXT
Credits.TRS  PC0606P     PO0205.TXT  PO0503.TXT  PO0710.TXT   POS0401.CXT
PC0101P      PC0607P     PO0206S     PO0504S     PO0711S      POS0402.CXT
PC0102P      PC0608P     PO0206.TXT  PO0504.TXT  PO0711.TXT   POS0403.CXT
PC0103P      PC0609P     PO0207S     PO0505S     PO0712S      POS0404.CXT
PC0104P      PC0610P     PO0207.TXT  PO0505.TXT  PO0712.TXT   POS0405.CXT
PC0105P      PC0611P     PO0208S     PO0506S     PO0801S      POS0406.CXT
PC0106P      PC0612P     PO0208.TXT  PO0506.TXT  PO0801.TXT   POS0407.CXT
PC0107P      PC0701P     PO0209S     PO0507S     PO0802S      POS0408.CXT
PC0108P      PC0702P     PO0209.TXT  PO0507.TXT  PO0802.TXT   POS0409.CXT
PC0109P      PC0703P     PO0210S     PO0508S     PO0803S      POS0410.CXT
PC0110P      PC0704P     PO0210.TXT  PO0508.TXT  PO0803.TXT   POS0411.CXT
PC0111P      PC0705P     PO0211S     PO0509S     PO0804S      POS0501.CXT
PC0201P      PC0706P     PO0211.TXT  PO0509.TXT  PO0804.TXT   POS0502.CXT
PC0202P      PC0707P     PO0301S     PO0510S     PO0805S      POS0503.CXT
PC0203P      PC0708P     PO0301.TXT  PO0510.TXT  PO0805.TXT   POS0504.CXT
PC0204P      PC0709P     PO0302S     PO0511S     PO0806S      POS0505.CXT
PC0205P      PC0710P     PO0302.TXT  PO0511.TXT  PO0806.TXT   POS0506.CXT
PC0206P      PC0711P     PO0303S     PO0512S     PO0807S      POS0507.CXT
PC0207P      PC0712P     PO0303.TXT  PO0512.TXT  PO0807.TXT   POS0508.CXT
PC0208P      PC0801P     PO0304S     PO0601S     PO0808S      POS0509.CXT
PC0209P      PC0802P     PO0304.TXT  PO0601.TXT  PO0808.TXT   POS0510.CXT
PC0210P      PC0803P     PO0305S     PO0602S     PO0809S      POS0511.CXT
PC0211P      PC0804P     PO0305.TXT  PO0602.TXT  PO0809.TXT   POS0512.CXT
PC0301P      PC0805P     PO0306S     PO0603S     PO0810S      POS0601.CXT
PC0302P      PC0806P     PO0306.TXT  PO0603.TXT  PO0810.TXT   POS0602.CXT
PC0303P      PC0807P     PO0307S     PO0604S     PO0811S      POS0603.CXT
PC0304P      PC0808P     PO0307.TXT  PO0604.TXT  PO0811.TXT   POS0604.CXT
PC0305P      PC0809P     PO0308S     PO0605S     PO0812S      POS0605.CXT
PC0306P      PC0810P     PO0308.TXT  PO0605.TXT  PO0812.TXT   POS0606.CXT
PC0307P      PC0811P     PO0309S     PO0606S     POS0101.CXT  POS0607.CXT
PC0308P      PC0812P     PO0309.TXT  PO0606.TXT  POS0102.CXT  POS0608.CXT
PC0309P      PO0101S     PO0310S     PO0607S     POS0103.CXT  POS0609.CXT
PC0310P      PO0101.TXT  PO0310.TXT  PO0607.TXT  POS0104.CXT  POS0610.CXT
PC0311P      PO0102S     PO0311S     PO0608S     POS0105.CXT  POS0611.CXT
PC0401P      PO0102.TXT  PO0311.TXT  PO0608.TXT  POS0106.CXT  POS0612.CXT
PC0402P      PO0103S     PO0401S     PO0609S     POS0107.CXT  POS0701.CXT
PC0403P      PO0103.TXT  PO0401.TXT  PO0609.TXT  POS0108.CXT  POS0702.CXT
PC0404P      PO0104S     PO0402S     PO0610S     POS0109.CXT  POS0703.CXT
PC0405P      PO0104.TXT  PO0402.TXT  PO0610.TXT  POS0110.CXT  POS0704.CXT
PC0406P      PO0105S     PO0403S     PO0611S     POS0111.CXT  POS0705.CXT
PC0407P      PO0105.TXT  PO0403.TXT  PO0611.TXT  POS0201.CXT  POS0706.CXT
PC0408P      PO0106S     PO0404S     PO0612S     POS0202.CXT  POS0707.CXT
PC0409P      PO0106.TXT  PO0404.TXT  PO0612.TXT  POS0203.CXT  POS0708.CXT
PC0410P      PO0107S     PO0405S     PO0701S     POS0204.CXT  POS0709.CXT
PC0411P      PO0107.TXT  PO0405.TXT  PO0701.TXT  POS0205.CXT  POS0710.CXT
PC0501P      PO0108S     PO0406S     PO0702S     POS0206.CXT  POS0711.CXT
PC0502P      PO0108.TXT  PO0406.TXT  PO0702.TXT  POS0207.CXT  POS0712.CXT
PC0503P      PO0109S     PO0407S     PO0703S     POS0208.CXT  POS0801.CXT
PC0504P      PO0109.TXT  PO0407.TXT  PO0703.TXT  POS0209.CXT  POS0802.CXT
PC0505P      PO0110S     PO0408S     PO0704S     POS0210.CXT  POS0803.CXT
PC0506P      PO0110.TXT  PO0408.TXT  PO0704.TXT  POS0211.CXT  POS0804.CXT
PC0507P      PO0111S     PO0409S     PO0705S     POS0301.CXT  POS0805.CXT
PC0508P      PO0111.TXT  PO0409.TXT  PO0705.TXT  POS0302.CXT  POS0806.CXT
PC0509P      PO0201S     PO0410S     PO0706S     POS0303.CXT  POS0807.CXT
PC0510P      PO0201.TXT  PO0410.TXT  PO0706.TXT  POS0304.CXT  POS0808.CXT
PC0511P      PO0202S     PO0411S     PO0707S     POS0305.CXT  POS0809.CXT
PC0512P      PO0202.TXT  PO0411.TXT  PO0707.TXT  POS0306.CXT  POS0810.CXT
PC0601P      PO0203S     PO0501S     PO0708S     POS0307.CXT  POS0811.CXT
PC0602P      PO0203.TXT  PO0501.TXT  PO0708.TXT  POS0308.CXT  POS0812.CXT
PC0603P      PO0204S     PO0502S     PO0709S     POS0309.CXT

```I see that now the .trs files haven't been changed, but everything else has.

---

### Post by detroit/zero on 2008-12-06
Well, a little investigating shows I was wrong to say these files are being renamed. There's a level of directory structure being stripped off at the top. Since I'm sure my terminology is wrong, allow me to illustrate:```
[COLOR=Blue]MyFolder[/COLOR]
|-- [COLOR=Red]XXX##_##[/COLOR]
|   |-- XX####.TXT
|   |-- [COLOR=SeaGreen]XX####X[/COLOR]
|   |   |-- XX#####.SND
|   |   `-- (there's about 50 or 100 of these)
|   `-- XXX####.CXT
|-- [COLOR=Red]XXX##_##[/COLOR]
|   |-- XX####.TXT
|   |-- [COLOR=SeaGreen]XX####X[/COLOR]
|   |   |-- XX#####.SND
|   |   `-- (so on and so forth)
|   `-- XXX####.CXT
```It's that folder in red that's being removed, and the files/folders contained in it are being copied to the iso without their "container". All the other subfolders (green) that have various files in them remain intact.

How can I maintain the original directory structure when creating this image?

After maybeway36's advice, the command I'm using to create this iso is:```
mkisofs -J -r -o ISONAME.iso ./*
```

---

### Post by 4t0m1c_w07f on 2008-12-06
Just use brasero and when you choose you're device just choose file... :)

---

### Post by detroit/zero on 2008-12-06
> **4t0m1c_w07f said:**
> Just use brasero and when you choose you're device just choose file... :)
Right.. that's always an option, but I'm looking for help with the command line method.

---

### Post by geirha on 2008-12-06
With that directory structure, your command is expanded to 
```
mkisofs -J -r -o ISONAME.iso ./XXX##_## ./XXX##_##
```
In other words, mkisofs are getting two directories as arguments, and mkisofs will only add the content of those directories, not the directories themselves. If you try with
```
mkisofs -J -r -o ISONAME.iso .
```
It will add all files and directories in the directory '.' instead. And '.' is of course the current-directory, and the directories inside it should be preserved. If you have any hidden files or directories in '.', they will be added too.

BTW, it has changed name from mkisofs to genisoimage, so if you want to read the man-page, it's ```
man genisoimage
```

---

### Post by detroit/zero on 2008-12-06
> **geirha said:**
> With that directory structure, your command is expanded to 
```
mkisofs -J -r -o ISONAME.iso ./XXX##_## ./XXX##_##
```In other words, mkisofs are getting two directories as arguments, and mkisofs will only add the content of those directories, not the directories themselves. If you try with
```
mkisofs -J -r -o ISONAME.iso .
```It will add all files and directories in the directory '.' instead. And '.' is of course the current-directory, and the directories inside it should be preserved. If you have any hidden files or directories in '.', they will be added too.That's where I messed up. I was inside the main folder containing all these various other folder and using the ./*, as you pointed out. I tried it your way and it worked like a charm.

---


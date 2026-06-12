---
title: "Half Life 2 and Wine"
date: 2006-06-01
forum: Gaming &amp; Leisure
---

### Post by johnwards on 2006-06-01
Busy trying out wine on a fresh Dapper install.

Now I installed Wine as per this:

[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam)

So I have added these to my sources:

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

Then I did the following:

sudo apt-get install wine

I got this back:
```
johnwards@johnwards-desktop:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  wine: Depends: libartsc0 (>= 1.5.2-0) but it is not installable
E: Broken packages

```

How odd I thought...

I have the current sources (and I have ran apt-get update)

```

deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

I thought I'd do a bit of a dodge...so...i downloaded libartsc0_1.5.2-0ubuntu1_i386.deb and did this
 
 sudo dpkg -i libartsc0_1.5.2-0ubuntu1_i386.deb

Then apt-get install wine worked fine (Downloading it from winehq as well)

Running winecfg gave me my .wine dir

Now I download the transgaming Active x thingy as said and untargz it in the dir as told too...

Now it says remove other Mozilla activex dlls as they may not work...doesn't tell you how though so I skipped this bit.

So I run wine regsvr32 mozctlx.dll

All is well so far..

Now I transgress from the instructions as I have steam and hl2 on my DVD so I just:

wine /cdrom/steam.exe

Steam gets installed OK.

now I install hl2

wine /cdrom/hl2.exe and I get:

```
johnwards@johnwards-desktop:~/.wine/drive_c/Program Files/mozcontrol$ wine /cdrom/hl2.exe
fixme:msi:MsiInstallProductW L"Z:\\cdrom\\hl2.msi" L" WISE_SETUP_EXE_PATH=Z:\\cdrom\\hl2.exe"
err:msi:msiobj_release Invalid handle!
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
err:msidb:get_tablecolumns couldn't load _Columns table
```

Now I have googled on this and I can find no one with that same error

I also tried:

wine msiexec /i /cdrom/hl2.msi 

and got the same error.

Most grumpy at this thought I was getting on so well

Any ideas?

---

### Post by eqisow on 2006-06-01
If you bought the DVD, can you still download it via Steam? If so, you could try that. If not, you could try coppying the contents of the CD from the HD and installing from there. There may be some kind of copy protection scheme giving problems.

---

### Post by GameGod on 2006-06-01
Yeah, if you have a valid Steam account and have installed HL2 before, you can just download it through Steam. (That's what I ended up having to do...)

---

### Post by ubu-for on 2006-06-01
> 
sudo apt-get install wine


Try Synaptic!

---


---
title: "[SOLVED] cannot update anymore"
date: 2008-10-02
forum: Desktop Environments
---

### Post by roberto.eiberle on 2008-10-02
whenever I try to update any program I get the following error message:


E: /var/cache/apt/archives/libvlc0_0.8.6.release.c-0ubuntu5.2_i386.deb: files list file for package `libmlt-data' is missing final newline


and nothing gets done.

I would much appreciate any help to correct this, thanks in advance

---

### Post by iponeverything on 2008-10-02
Try to fix the list file that is giving you issues.

first backup the file --

sudo mkdir /root/bkup
sudo cp -a /var/lib/dpkg/info/libmlt-data.list /root/bkup

Lets try to fix it:

cd /var/cache/apt/archives
sudo dpkg --contents libmlt-data*.deb |awk '{print $6}' |sed s/^.// |sed s/\\/$// > /tmp/listfile
sudo echo /. > /var/lib/dpkg/info/libmlt-data.list
sudo cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list

see if that fixes it.

---

### Post by roberto.eiberle on 2008-10-02
> **iponeverything said:**
> Try to fix the list file that is giving you issues.

first backup the file --

sudo mkdir /root/bkup
sudo cp -a /var/lib/dpkg/info/libmlt-data.list /root/bkup

Lets try to fix it:

cd /var/cache/apt/archives
sudo dpkg --contents libmlt-data*.deb |awk '{print $6}' |sed s/^.// |sed s/\\/$// > /tmp/listfile
sudo echo /. > /var/lib/dpkg/info/libmlt-data.list
sudo cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list

see if that fixes it.
roberto@roberto:~$ sudo echo /. > /var/lib/dpkg/info/libmlt-data.list
bash: /var/lib/dpkg/info/libmlt-data.list: Permission denied
roberto@roberto:~$ sudo cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list
bash: /var/lib/dpkg/info/libmlt-data.list: Permission denied
roberto@roberto:~$ 

as you can see I get permission denied in the last 2 steps up to there o.k

the backup was created. btw I found the following in my lost and found folder wicj I think might be related

50994c17646458e4a5722e5ea4603e18  usr/share/doc/libmlt++0.2.4/README.Debian
8e4ff321053ab2fa67cc22bfdc429fa7  usr/share/doc/libmlt++0.2.4/copyright
a08f8b3e05c8f78efbe80fe1b2631d4b  usr/share/doc/libmlt++0.2.4/changelog.Debian.gz
3b6c9dce9616300b53ae1edaa414ff0c  usr/lib/libmlt++.so.0.2.4

---

### Post by iponeverything on 2008-10-02
> **roberto.eiberle said:**
> roberto@roberto:~$ sudo echo /. > /var/lib/dpkg/info/libmlt-data.list
bash: /var/lib/dpkg/info/libmlt-data.list: Permission denied
roberto@roberto:~$ sudo cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list
bash: /var/lib/dpkg/info/libmlt-data.list: Permission denied
roberto@roberto:~$ 

as you can see I get permission denied in the last 2 steps up to there o.k

the backup was created. btw I found the following in my lost and found folder wicj I think might be related

50994c17646458e4a5722e5ea4603e18  usr/share/doc/libmlt++0.2.4/README.Debian
8e4ff321053ab2fa67cc22bfdc429fa7  usr/share/doc/libmlt++0.2.4/copyright
a08f8b3e05c8f78efbe80fe1b2631d4b  usr/share/doc/libmlt++0.2.4/changelog.Debian.gz
3b6c9dce9616300b53ae1edaa414ff0c  usr/lib/libmlt++.so.0.2.4


I do think that it is related. It looks like you had a little file corruption.

Try this:

sudo bash
cd /var/cache/apt/archives
dpkg --contents libmlt-data*.deb |awk '{print $6}' |sed s/^.// |sed s/\\/$// > /tmp/listfile
echo /. > /var/lib/dpkg/info/libmlt-data.list
cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list
rm /var/lib/dpkg/info/libmlt-data.list
echo /. > /var/lib/dpkg/info/libmlt-data.list
cat /tmp/listfile >> /var/lib/dpkg/info/libmlt-data.list
exit

---

### Post by roberto.eiberle on 2008-10-02
the message changed but still does'nt work

E: /var/cache/apt/archives/libvlc0_0.8.6.release.c-0ubuntu5.2_i386.deb: files list file for package `libmlt-data' contains empty filename

complete result when I try to install any update or program

Reading changelogs... Done
(Reading database ...
dpkg: serious warning: files list file for package `libmlt++0.2.4' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `kdenlive' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/vlc_0.8.6.release.c-0ubuntu5.2_i386.deb (--unpack):
 files list file for package `libmlt-data' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/vlc_0.8.6.release.c-0ubuntu5.2_i386.deb
Processing was halted because there were too many errors.


It seems all due to a crash of kdenlive, which stopped working but I cannot eliminate it as it is not in the fileslist it is somehow being reported as existent and nonexistent at the same time.

---

### Post by iponeverything on 2008-10-02
Let try this a different way:

find and download the old version of the libmlt-data deb file.
then try the process with that. It appears that maybe .deb was corrupt.

you can find it with google.

do

dpkg -l |grep libmlt-data 

to find the version that was installed or look at the file name in:

/var/cache/apt/archive 

for that file name.

---

### Post by roberto.eiberle on 2008-10-03
well, I tried this, but no chance, I cannot install or update anything, even unrelated to libmlt or kdenlive. dpkg always says too many errors. maybe I'll have to make the horrible decision to reinstall everything from scratch. In any case thank you very much for all the effort you put in this

---

### Post by iponeverything on 2008-10-03
that is a bummer. I know that there is a way to recover -- though I can find it at the moment.

---

### Post by roberto.eiberle on 2008-10-05
finally found a solution in google, " just put /var/lib/dpkg/info mlt-data in the trash " and I was able to uninstall the program and update everything. I probably have some useless files lying around somewhere but everything seems to work

---


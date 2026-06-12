---
title: "Ultimate Ubuntu-to-Fedora transition guide"
date: 2007-10-05
forum: Fedora/RedHat and derivatives
---

### Post by Frak on 2007-10-05
I started this guide to help those trying to transition from Ubuntu to Fedora, to feel more like home :)

[SIZE="5"]**Sudo**[/SIZE]
Goto
Applications->System Tools->Terminal and enter the following commands
```
su -
echo '**loginname** ALL=(ALL) ALL' >> /etc/sudoers
```
Where **loginname** is your login name, as mine would say 'frak
Also, make sure the ' sign stays at the beginning of the name.

Now you should be able to use sudo for common activities that require root access.

P.S. (**NOTE: HIGHLY NOT RECOMMENDED**) Use 'ALL=(ALL) NOPASSWD:ALL' if you don't want to be prompted a password.
"

[SIZE="5"]**Yum**[/SIZE]
**Yum** is Fedora's version of Apt.
Configure it to accept the default repositories with:
```
sudo rpm --import /etc/pki/rpm-gpg/*
```
It contains two repositories with no proprietary applications, but lets say you do...
```
sudo rpm -ivh http://rpm.livna.org/livna-release-7.rpm
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-livna
```

(NOTE: livna repos are not compatible with freshrpms repos)

If you want to update your system, run
```
sudo yum update
```
Or goto Applications->System Tools->Terminal

If you want to install software, run
```
sudo yum install name_of_software_here
```
Or, if you don't want to be asked "Are you sure?"
```
sudo yum -y install name_of_software_here
```

[SIZE="5"]**GCC**[/SIZE]
Fedora 7 comes with GCC 4.1 by default, but some require older versions such as 3.2, to install these, run.
```
sudo yum -y install compat-libstdc++-33 compat-libstdc++-296
```



Or 3.4
```
sudo yum install compat-gcc-34 compat-gcc-34-c++
```


[SIZE="5"]**Alsa**[/SIZE]
If Alsa doesn't work quite right, run
```
sudo yum update kernel alsa-lib alsa-utils
```
And see if that fixes your problem



[SIZE="5"]**TrueType**[/SIZE]
Just run
```
sudo yum -y install wget
wget http://corefonts.sourceforge.net/msttcorefonts-2.0-1.spec
sudo rpmbuild -bb msttcorefonts-2.0-1.spec
sudo rpm -ivh $HOME/rpmbuild/RPMS/noarch/msttcorefonts-2.0-1.noarch.rpm
sudo /etc/init.d/xfs restart
```

Fedora wants you to use Liberation Fonts, if these are not installed, run
```
sudo yum install liberation-fonts
```


[SIZE="5"]**RealPlayer**[/SIZE]
To install RealPlayer, download it from here: [http://www.real.com/linux/](http://www.real.com/linux/)
And choose
"Advanced Installation
RedHat Package"
And download it to your home folder

Then
```
sudo yum install compat-libstdc++-33
sudo rpm -ivh RealPlayer*.rpm
```


[SIZE="5"]**MP3 Players**[/SIZE]

XMMS: ```
sudo yum install xmms xmms-mp3 xmms-faad2
```

Audacious: ```
sudo yum install audacious audacious-plugins-nonfree*
```

RhythmBox - GStreamer-Plugins: ```
sudo yum install gstreamer-plugins-ugly gstreamer-plugins-bad
```

Amarok: ```
sudo yum install amarok amarok-extras-nonfree
```


[SIZE="5"]**Adobe Acrobat**[/SIZE]
Latest version is [8.1.1]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")
Linux->x86 .rpm->(Language) then click download
Save it to your Home directory
then
```
sudo rpm -ivh AdobeReader.*.rpm
```

If you choose the v.7, then you may have to edit a config file for it to work properly
```
sudo gedit /usr/local/Adobe/Acrobat7.0/bin/acroread
```

On line 418 change to
```
From:
   echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'
To:
   echo $mfile| sed 's/libgtk-x11-\([0-9]*\).0.so.0.\([0-9]*\)00.\([0-9]*\)\|\(.*\)/\1\2\3/g'
```

Line 643:
```
From:
   MIN_GTK_VERSION="240"
To:
   MIN_GTK_VERSION="2040"
```


[SIZE="5"]**NTFS**[/SIZE]
To read from NTFS properly, run
```
sudo yum install fuse fuse-libs ntfs-3g
```

NOTE: If you installed via DVD, NTFS support should be already enabled


[SIZE="5"]**Kernel Headers and Source**[/SIZE]
For Headers, Run
```
sudo yum install kernel-devel
```
For source via Yum, run
```
sudo yum install yum-utils
cd downloads
sudo yumdownloader --source kernel
```


[SIZE="5"]**Flash and Java**[/SIZE]
Flash
```
sudo rpm -ivh http://linuxdownload.adobe.com/adobe-release/adobe-release-1.0-0.noarch.rpm
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-adobe-linux
sudo yum install flash-plugin
```

Java
Download from: [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)
Select: Java Runtime Environment (JRE)
Save to your Home directory

```
sudo yum -y install compat-libstdc++-33
sh jre-6u3-linux-i586.bin
(hit 'space' till the end, then type 'yes')
sudo mv -f jre1.6* /opt/jre1.6
sudo ln -s /opt/jre1.6/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/libjavaplugin_oji.so

```

Fedora will automatically run GNU Java before Sun Java, to change this
```
sudo /usr/sbin/alternatives --install /usr/bin/java java /opt/jre1.6/bin/java 2
echo 2 | sudo /usr/sbin/alternatives --config java
java -version
java version "1.#"
Java(TM) SE Runtime Environment (build 1.#)
Java HotSpot(TM) Client VM (build 1.#, mixed mode, sharing)
```

[SIZE="5"]**Frostwire**[/SIZE]
Follow the Java installation as said above, then
Download  and install frostwire from [Frostwire.com]("http://www.frostwire.com")
then run
```
sudo yum install -y libXp
```

If you run Fedora 8 w/ Nvidia card, and you get xcb_xlib_unlock as part of the error message, this is a bug, and I hope it gets fixed soon.

Hope this helps :)

---

### Post by pelle.k on 2007-10-07
Really nice! I did run fedora for the very first time a while ago, and this guide would have saved me some time back then!
Good work :)

---

### Post by jinx099 on 2007-10-09
You might want to also say what advantages Fedora has over Ubuntu, otherwise, why would people want to switch?  I like fedora because you get new versions of packages instead of just security updates.

---

### Post by karellen on 2007-10-11
nice and useful stuff :)

---

### Post by Antman on 2007-10-11
hmmm... makes me want to load Fedora and give it a spin... but I'll wait till version 8.  ;)

---

### Post by Frak on 2007-11-06
Bump

---

### Post by Kingsley on 2007-11-09
Nice work.

Free bump

---

### Post by Frak on 2007-11-09
Thanks, I'm going to work on it a bit more since Fedora 8 is out :)

---

### Post by FuturePilot on 2007-11-09
Frak you rock!:guitar:
I never would have thought I could install **Fedora** and get all my answers from the **Ubuntu** forum.:lolflag:
Fedora 8 is really nice. I'm using it right now.

---

### Post by SunnyRabbiera on 2007-11-09
but YUM sucks!
I definitely prefer apt.

---

### Post by Incense on 2007-11-09
> **SunnyRabbiera said:**
> but YUM sucks!
I definitely prefer apt.

Why does yum suck? I've never used it.

---

### Post by Frak on 2007-11-09
> **Incense said:**
> Why does yum suck? I've never used it.
It doesn't handle packages as well as apt, and IMHO it's slower.

---

### Post by SunnyRabbiera on 2007-11-11
> **Frak said:**
> It doesn't handle packages as well as apt, and IMHO it's slower.
uh huh, thus are my reasons, apt is definitely better for things like dependencies and junk.

---

### Post by eljoeb on 2007-11-11
> **Frak said:**
> It doesn't handle packages as well as apt, and IMHO it's slower.

Yum with F8 is a good deal faster.

---


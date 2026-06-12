---
title: "Kaffeine - how to get dvd to play"
date: 2006-08-08
forum: Desktop Environments
---

### Post by geovino on 2006-08-08
What do I have to do to get Kaffeine to play dvds? Totem wants to come up but it can't either. I thought I had all the lib files I needed. What else needs to be done?

---

### Post by computergroove on 2006-08-08
Get automatix and download the "nonfree codec" package. Post your results if it doesnt work.

---

### Post by PCalitrack on 2006-08-08
The Totem player should play dvd's once you use Automatix to install all the require codecs. Infact the player should even come up right when you insert a  cd.

Instructions for Automatix install:
Issue these 3 commands:
wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

---

### Post by shoki on 2006-08-08
I would be curious how to add these codecs without using automatix. I use automatix and it has been great but still it would be nice to know what is being done automatixly... :)

---

### Post by Zlatan on 2006-08-09
> **shoki said:**
> I would be curious how to add these codecs without using automatix. I use automatix and it has been great but still it would be nice to know what is being done automatixly... :)

try [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by scxtt on 2006-08-09
all i did:
[indent]sudo aptitude install libdvdnav4 libdvdplay0 libdvdread3[/indent]
then ran:
[indent]sudo /usr/share/doc/libdvdread3/examples/install-css.sh[/indent]
then popped in a DVD ...

```
:> aptitude search libdvd
i   libdvdcss2                                    - a portable abstraction library for DVD decryption
p   libdvdnav-dev                                 - The DVD navigation library, development package
i   libdvdnav4                                    - The DVD navigation library
i   libdvdplay0                                   - portable abstraction library for DVD menus support
p   libdvdplay0-dev                               - development files for libdvdplay0
v   libdvdread-dev                                -
i   libdvdread3                                   - Simple foundation for reading DVDs
p   libdvdread3-dev                               - Simple foundation for reading DVDs
```

---

### Post by geovino on 2006-08-09
> **PCalitrack said:**
> The Totem player should play dvd's once you use Automatix to install all the require codecs. Infact the player should even come up right when you insert a  cd.

Instructions for Automatix install:
Issue these 3 commands:
wget [http://www.getautomatix.com/files/automatix-installer](http://www.getautomatix.com/files/automatix-installer)
chmod 755 ~/automatix-installer
./automatix-installer

I did that then I get this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
davek@davek-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
davek@davek-desktop:~$ sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
davek@davek-desktop:~$

how do I get it to run with superuser privilege? I thought I was in sudo already.

What is odd is I had Kaffeine running last week the day after I installed Ubuntu, then with trying to get all the codec and lib files something happened and it stopped working. All these files should be installed by default so people don't have to go through all this.

---

### Post by LeonHeart on 2006-08-09
Just follow these steps:

1) Enable the universe and multiverse repositories. [Instructions]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories")

2) Download and install [libdvdcss]("http://download.videolan.org/pub/libdvdcss/1.2.9/deb/libdvdcss2_1.2.9-1_i386.deb")

3) Open the Synaptic Package Manager and install:
**libdvdread3, libdvdnav4, libdvdplay**

4) Download and extract [This Codec Pack]("http://www3.mplayerhq.hu/MPlayer/releases/codecs/essential-20060611.tar.bz2") to /usr/lib/win32

5) Open the Synaptic Package Manager and install:
** Kaffeine, Kaffeine-xine**


And you are done. You now have a fully charged media player
that can play everything from avi files to DVDs....

I hope I helped........

---

### Post by geovino on 2006-08-09
I'll try that. 

I just went to Synaptic and I got this error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

I've tried to run it and it doesn't work. Am I doing it right?

$ dpkg --configure -a

I try to run that and it won't run. Any clues?

---

### Post by geovino on 2006-08-09
My source.list has only one entry:
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

but I have backup source lists with all the other repository addresses. I'm getting confused about where to make changes.

So until I get synpatic to open I can't do anything. 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

this is what I have to fix. Why doesn't this command, dpkg --configure -a
run properly?

---

### Post by etank on 2006-08-09
Try running ```
sudo dpkg --configure -a
```

---

### Post by geovino on 2006-08-09
Thanks, I did that and this is what I get:

davek@davek-desktop:~$ sudo dpkg --configure -a
Password:
Setting up libmjpegtools0c2a (1.8.0-0.0ubuntu1) ...

Setting up vorbis-tools (1.1.1-3) ...

Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...

...and its still hanging there. Doesn't it have to do more and when complete it goes back to the prompt?

I closed the terminal and went back to synaptic and I get the same error message. 

What should I do?

---

### Post by geovino on 2006-08-09
I finally got the dvd to open Totem and play. Yeah!

But I'm watching this Pearl Jam 2000 dvd and I'm noticing that the sound is slightly off-sink with their singing in the video. I haven't seen that before. have you?

I just ried it with Kaffeine and it works fine. How do I make Kaffeine the default?

Thanks.

---


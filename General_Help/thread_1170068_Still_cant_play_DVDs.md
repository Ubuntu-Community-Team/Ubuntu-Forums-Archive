---
title: "Still cant play DVDs"
date: 2009-05-25
forum: General Help
---

### Post by Sentience on 2009-05-25
I followed the instructions, cut and pasted the command line from Medibuntu, but it still wont play.


"The source seems encrypted and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I thought I already added that.

---

### Post by theozzlives on 2009-05-25
What's it doing when you try? What player are you using, etc.?

---

### Post by Sentience on 2009-05-25
It says an error occured, then the same thing I typed above.

I am using the 64 bit version, which might be a bit buggier.

I tried VCL, Totem, and others.

---

### Post by lisati on 2009-05-25
The only thing I could think of was this link: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by Sentience on 2009-05-25
I followed the instructions in that link, and then this.


Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.

---

### Post by alphacrucis2 on 2009-05-25
> **Sentience said:**
> I followed the instructions in that link, and then this.


Playback failure:
VLC cannot set the DVD's title. It possibly cannot decrypt the entire disk.
File reading failed:
VLC could not read the file.
File reading failed:
VLC could not read the file.

You need the package libdvdcss2. If you look in synaptic can you see if it actually got installed. If not then install it. It should normally get installed with ubuntu-restricted-extras.

Edit - Whoops - sorry the restricted-extras package doesn't include libdvdcss2.

---

### Post by asmoore82 on 2009-05-25
to double-check that libdvdcss is properly installed:
```
dpkg-query -s libdvdcss2
```

---

### Post by lisati on 2009-05-25
Which version of Ubuntu are you using?

Based on [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) we have the following instructions for Ubuntu 9.04 (older versions have different instructions):

Run the following two lines from the terminal:
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```
This will (usually) be sufficient to install libdvdcss2

---

### Post by Sentience on 2009-05-25
I dont see it installed. Ive followed every set of directions I can find and I just dont see it.

When I try to install it, it says this.


jinn@anon-desktop:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

---

### Post by Sentience on 2009-05-25
> **lisati said:**
> Which version of Ubuntu are you using?

Based on [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) we have the following instructions for Ubuntu 9.04 (older versions have different instructions):

Run the following two lines from the terminal:
```
sudo apt-get install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

```
This will (usually) be sufficient to install libdvdcss2



ok, I tried this and it did something....


jinn@anon-desktop:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jinn@anon-desktop:~$ 
jinn@anon-desktop:~$ 
jinn@anon-desktop:~$ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
jinn@anon-desktop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2009-05-25 19:18:34--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 91.121.62.209, 88.191.79.39, 88.191.82.11
Connecting to packages.medibuntu.org|91.121.62.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 37252 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-ofAfcR/libdvdcss.deb'

100%[======================================>] 37,252      66.9K/s   in 0.5s    

2009-05-25 19:18:35 (66.9 KB/s) - `/tmp/dvdcss-ofAfcR/libdvdcss.deb' saved [37252/37252]

(Reading database ... 124544 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using .../dvdcss-ofAfcR/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
jinn@anon-desktop:~$ 





But its still not working. Same error message when I open VCL.

---

### Post by Sentience on 2009-05-25
So if its not libdvdcss2, what else could it be?

I am using 9.04 btw. Jaunty.



.

---

### Post by Steelmourne on 2009-05-25
Load up ubuntu help and choose the music, video and photos category, then playing dvd's from the contents menu. Follow the instructions.

---

### Post by scouser73 on 2009-05-26
From what I remember, if you've entered the commands in Terminal correctly then you should be using Totem Xine for playing DVD discs which is in the repositories.

---

### Post by hyperdude111 on 2009-05-26
sudo apt-get install ubuntu-restricted-extras

---

### Post by Soul-Sing on 2009-05-26
> **hyperdude111 said:**
> sudo apt-get install ubuntu-restricted-extras

+1

you need:  -Gstreamer extra plugins

           -Gstreamer ffmpeg video plugin 

and as said: libdvdcss2.

smplayer should play any dvd now.....

---

### Post by growled on 2009-05-26
> **hyperdude111 said:**
> sudo apt-get install ubuntu-restricted-extras

Another +1 here. That should solve your problem.

---


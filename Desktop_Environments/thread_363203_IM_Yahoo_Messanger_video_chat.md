---
title: "IM_Yahoo Messanger video chat"
date: 2007-02-16
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2007-02-16
Hi All,

Is there any one successful in video chat on yahoo messanger in Ubuntu? I request you to please post the steps you followed.

Any one please help.

Thanks in advance,

Regards,

Swaroop Kunduru.

---

### Post by fakie_flip on 2007-03-03
nope, but if your webcam has the proper driver (this requires compiling kernel modules sometimes), and it works, then you can use amsn and your webcam will be broadcasted on the msn protocol

---

### Post by joselin on 2007-03-03
> **fakie_flip said:**
> nope, but if your webcam has the proper driver (this requires compiling kernel modules sometimes), and it works, then you can use amsn and your webcam will be broadcasted on the msn protocol

With amsn you only can see the webcam, but you can't hear nothing because is not yet implemented.

---

### Post by Arup on 2007-03-03
Gayachi can be installed via automatix, promises voice with Yahoo but I haven't tried it out.

---

### Post by fakie_flip on 2007-03-05
> **joselin said:**
> With amsn you only can see the webcam, but you can't hear nothing because is not yet implemented.

Right, but it is better than having nothing. If you want voice chat, use Skype. [www.skype.com](www.skype.com) has a repository you can add to your /etc/apt/sources.list and it will let you voice chat with others no matter what os they are using such as windows, linux, and osx because they all have skype that runs on those OSs. I'm not too worried about it until get my webcam working. I have spent so many hours and different times trying to get it working by compiling kernel modules. Not even the mailing list for the drivers could help me. I got loads of errors from syslog about the kernel.

---

### Post by iamhugeinjapan on 2007-03-05
> **Arup said:**
> Gayachi can be installed via automatix, promises voice with Yahoo but I haven't tried it out.

Just to clarify:

The program is called GyachE (Gyach Enhanced)
[http://www.phrozensmoke.com/projects/pyvoicechat/](http://www.phrozensmoke.com/projects/pyvoicechat/)

There is also the fork that Automatix installs called GYachI  (GyachE Improved)
[http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)

GyachE is a fork of the original project Gyach which is not as feature filled.
[http://gyach.bc2va.org/](http://gyach.bc2va.org/)

---

### Post by loell on 2007-03-05
or you can just install gyachi , without installing automatix

[http://gyachi.sourceforge.net/download.shtml]("http://gyachi.sourceforge.net/download.shtml")

it has an edgy and dapper package

---

### Post by ragadanga63 on 2007-03-09
kabayan loell:

I've been using gyachi which worked fine until i replaced my webcam with a Dlink DSB-C310.  Tried using it in gyachi but but got this error message:

"GyachI (Webcam Broadcaster):

An error occurred at 'ioctl VIDIOSPICT'. Could not set camera properties."

Is this a driver problem?  If it is how do i install driver for my webcam?

Thanks.

---

### Post by loell on 2007-03-09
> **ragadanga63 said:**
> kabayan loell:

I've been using gyachi which worked fine until i replaced my webcam with a Dlink DSB-C310.  Tried using it in gyachi but but got this error message:

"GyachI (Webcam Broadcaster):

An error occurred at 'ioctl VIDIOSPICT'. Could not set camera properties."

Is this a driver problem?  If it is how do i install driver for my webcam?

Thanks.

ah i see, does Dlink DSB-C310 webcam worked on other webcam base applications? like ekiga?

---

### Post by ragadanga63 on 2007-03-10
I tried CAMSTREAM.  The cam wasn't in the least of video sources.  Must be driver problem?

---

### Post by loell on 2007-03-11
yes, most probably

---

### Post by loell on 2007-03-11
> **ragadanga63 said:**
> I tried CAMSTREAM.  The cam wasn't in the least of video sources.  Must be driver problem?

have you tried the ov511 driver? its compatible they say :)

---

### Post by ragadanga63 on 2007-03-13
(I tried CAMSTREAM. The cam wasn't in the _least _of video sources. Must be driver problem?)  Ooops.  I meant "list" not "least".

Thanks pre, I'll try ov511.

---

### Post by Doug11 on 2007-03-13
Have you tried Kopete, with it you can chose which protocol you want to use, ie. msn, icq, yahoo etc. It has webcam and also aMSN works for me as well.

---

### Post by fakie_flip on 2007-03-14
Same thing happens with gyachE Improved as Gaim. I installed it from a deb for Edgy, and it won't let me in any chat rooms.

  ** The chat room is full. Please try again later.: 'Alabama:7' **
  ** The chat room is full. Please try again later.: 'Alabama:64' **
  ** The chat room is full. Please try again later.: 'Florida:46' **
  ** The chat room is full. Please try again later.: 'Florida:125' **
  ** The chat room is full. Please try again later.: 'Florida:76' **
  ** The chat room is full. Please try again later.: 'Florida:76' **
  ** The chat room is full. Please try again later.: 'Florida:76' **
  ** The chat room is full. Please try again later.: 'Kentucky:3' **
  ** The chat room is full. Please try again later.: 'Linux, FreeBSD, Solaris:1' **
  ** The chat room is full. Please try again later.: 'Linux, FreeBSD, Solaris:2' **
  ** The chat room is full. Please try again later.: 'Linux, FreeBSD, Solaris:3' **
  ** The chat room is full. Please try again later.: 'Linux, FreeBSD, Solaris:4' **

Gaim does this too, but gives me this message. The chat rooms are not full. I get the errors no matter how many people are in the chat rooms.

Failed to join chat
Maybe the room is full

I would use java chat for yahoo through Firefox, but that does not exist anymore.

---

### Post by mocksxxvii on 2008-01-16
hello please help me my cam is A4TECH ,,, when i use my cam its not work

GyachI (Webcam Broadcaster):

An error occurred at 'ioctl VIDIOSPICT'. Could not set camera properties."

Is this a driver problem? If it is how do i install driver for my webcam?

Thanks.

tell me the problem ... and the solution pls ... pls ... pls...

---

### Post by loell on 2008-01-16
first, make sure that your webcam is compatible with linux

if your webcam is working properly on other linux webcam applications then this is a gyachi specific bug. if this is the case then you'll gonna have to wait for gyachi to enhance its webcam detection.

---


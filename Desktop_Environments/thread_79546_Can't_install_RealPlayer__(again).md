---
title: "Can't install RealPlayer  (again)"
date: 2005-10-20
forum: Desktop Environments
---

### Post by seatea on 2005-10-20
I just installed Ubuntu 5.0.4 on a partitiion of my PM G4. It  was not a smooth installation, but things finally stated working after a few failed attempts. I have been trying to install RealPlayer and after following  the Unofficial Ubuntu Guide advise and searching across multiple forums, I still cannot get it to install. I am totally new to Linux with only some  background  gleaned  from a couple of books,  which are  not helping me at the moment. I  don't know what I am missing. I have two  files downloaoded  on my computer in my home  folder. One is "realplay-10.0.6.776-linux-2.2-libc6-gcc32-i586.bin". The  other is "RealPlayer10GOLD.bin". I cannot  get it to either to run by double  clicking  and the  other  methods I have tried to use to get these files to install will not work for me. What am I missing? I would greatly appreciate some one providing a step by step approach to installing  RealPlayer or  pointing out  what  i am not doing  right.

Thanks.

---

### Post by mokeyjoe on 2005-10-20
Hi there!

Have you installed anything else succesfully? Or can't you install anything at all.

---

### Post by Sirin on 2005-10-20
[QUOTE=seatea]I just installed Ubuntu 5.0.4 on a partitiion of my PM G4. It  was not a smooth installation, but things finally stated working after a few failed attempts. I have been trying to install RealPlayer and after following  the Unofficial Ubuntu Guide advise and searching across multiple forums, I still cannot get it to install. I am totally new to Linux with only some  background  gleaned  from a couple of books,  which are  not helping me at the moment. I  don't know what I am missing. I have two  files downloaoded  on my computer in my home  folder. One is "realplay-10.0.6.776-linux-2.2-libc6-gcc32-i586.bin". The  other is "RealPlayer10GOLD.bin". I cannot  get it to either to run by double  clicking  and the  other  methods I have tried to use to get these files to install will not work for me. What am I missing? I would greatly appreciate some one providing a step by step approach to installing  RealPlayer or  pointing out  what  i am not doing  right.

Thanks.[/QUOTE]

In the terminal, have you tried this?

Copy and paste this into your terminal and press enter, and then type your password ([COLOR=Red]**NOTE: Make sure that "RealPlayer10GOLD.bin" is in your Home folder.**[/COLOR]):
> 
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin


---

### Post by seatea on 2005-10-20
Thank you for your comments. I  haven't tried to install anything else so  far, except for the  updates  to Ubuntu 5.0.4. That went ok. I tried the  "chmod a+x RealPlayer10GOLD.bin" command followed by the "sudo ./RealPlayer10GOLD.bin" command, but only got the reply "./RealPlayer10GOLD.bin: ./RealPlayer10GOLD.bin: cannot execute binary file". I went through the steps outlined in the Ubuntu Unofficial guide again and after a long string of text it ended "E: Package realplayer has no installation candidate". I then did the gnome panel refresh command and once again nothing. Any idea  what I am doing  wrong? I  do have the  file RealPlayer 10Gold.bin in my home  folder.

---

### Post by chinman on 2005-10-21
I did follow Sirin's installation steps. It shows these messegs: 
Extracting files for RealPlayer installation...
Error: short read (4703717/5646139 bytes) (Invalid argument)
.
What I can do?

---

### Post by Sirin on 2005-10-21
[QUOTE=seatea]
Thank you for your comments. I haven't tried to install anything else so far, except for the updates to Ubuntu 5.0.4. That went ok. I tried the "chmod a+x RealPlayer10GOLD.bin" command followed by the "sudo ./RealPlayer10GOLD.bin" command, but only got the reply "./RealPlayer10GOLD.bin: ./RealPlayer10GOLD.bin: cannot execute binary file". I went through the steps outlined in the Ubuntu Unofficial guide again and after a long string of text it ended "E: Package realplayer has no installation candidate". I then did the gnome panel refresh command and once again nothing. Any idea what I am doing wrong? I do have the file RealPlayer 10Gold.bin in my home folder.[/QUOTE]

Where did you download the file from? I got mine from [http://www.realplayer.com/](http://www.realplayer.com/) and it works fine.
If you downloaded it from any other source (e.g., The Repositories), chances are, they may have had a corrupted version of the installation file. 

[QUOTE=chinman]I did follow Sirin's installation steps. It shows these messegs: 
Extracting files for RealPlayer installation...
Error: short read (4703717/5646139 bytes) (Invalid argument)
.
What I can do?[/QUOTE]

Your installation file seems to be corrupted. Have you tried deleting that file and downloading it again?

---

### Post by seatea on 2005-10-21
I installed the RealPlayer10GOLD.bin file from Real.com. I  can see it on my desktop and have moved it to my home  folder as well in attempts to get it to install. Neither place will work as far as being recognized by the apt-get command. I have  attempted this several times , but it  will not  install. Interestingly, I have  also  tried to install the Flash player using similar steps from the  Unofficial Ubuntu Guide and was unable to install it for the same reasons as the RealPlayer won't install with that method. There  seems  to be some problem with  the extra repositories in  the instructions, because  consistently I get the message that  there is  a problem which  seems to involve the  last two lines of the sources list, 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted. Both are listed  as being unable to "stat" and  unable to find. Does this offer any ideas on my problem with the installation?

I was able  to install the Firestarter firewall, although  I am not sure it ofers as much security as I would like to have. Specifically , I didn't see an option  for stealth mode.

---


---
title: "Quake 3 Arena Demo"
date: 2005-09-09
forum: Gaming &amp; Leisure
---

### Post by cadaver on 2005-09-09
What the hell do I do with this thing?  :???: 

linuxq3ademo-1.11-6.x86.gz.sh

---

### Post by KingBahamut on 2005-09-09
Open a terminal 

chmod 777 linuxq3ademo-1.11-6.x86.gz.sh

then 

sh linuxq3ademo-1.11-6.x86.gz.sh 
hit enter

---

### Post by Alacrity on 2005-09-09
What would everybody do without your help Bahamut?  My chmod went thru ok.  Then with sh, I get:

root@ubuntu:/home/john/Desktop # ls
linuxq3ademo-1.11-6.x86.gz.sh  Nexuiz
root@ubuntu:/home/john/Desktop # chmod 777 linuxq3ademo-1.11-6.x86.gz.sh
root@ubuntu:/home/john/Desktop # sh linuxq3ademo-1.11-6.x86.gz.sh
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
root@ubuntu:/home/john/Desktop #

Any suggestions?

---

### Post by Harleen on 2005-09-09
The Installer seems to try to open a graphical output, but isn't allowed to do so, because the X-Server belongs to your user and you running the setup as root. To install, you can 
1) try to install as user
or
2) install using "sudo sh linuxq3ademo-1.11-6.x86.gz.sh"
or
3) call "xhost +" on a shell with your standard user (NOT root!) and thus allowing everybody to open windows on your X-Server

---

### Post by Alacrity on 2005-09-09
Harleen,

Thanks for helping a NOOB.

I get:

root@ubuntu:/home/john # cd Desktop
root@ubuntu:/home/john/Desktop # ls
linuxq3ademo-1.11-6.x86.gz.sh  Nexuiz
root@ubuntu:/home/john/Desktop # sh linuxq3ademo-1.11-6.x86.gz.sh
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
root@ubuntu:/home/john/Desktop # sudo sh linuxq3ademo-1.11-6.x86.gz.sh
Warning: Tried to connect to session manager, Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
root@ubuntu:/home/john/Desktop #

Let me try to figure out your other two alternatives..............

---

### Post by Alacrity on 2005-09-09
Hmmmmmmmmmmmm.....

I am the only user..............

So, not sure how to implement the other two recommendations/alternatives..........

---

### Post by Alacrity on 2005-09-09
Came on non root.

Got this:

john@ubuntu:~/Desktop$ ls
linuxq3ademo-1.11-6.x86.gz.sh  Nexuiz
john@ubuntu:~/Desktop$ sh linuxq3ademo-1.11-6.x86.gz.sh
john@ubuntu:~/Desktop$

Seemed to take it............

Now where do I find it?

Am I a NOOB or what?

---

### Post by Harleen on 2005-09-10
I don't know that installer, but I assume, it has asked your for an install location. If you installed it as user it probably installed into /user/john/quake3demo or something similar. If you are totally lost, you can search for the startup file:
find ~ -name q3demo

---

### Post by Statik on 2005-09-10
I'm doing the same thing, and I have no location yet. The command opens another terminal window that lists some stuff, but it closes before I can read it. How can I send that output either to the same window, or keep the other window open?

Statik

---

### Post by Alacrity on 2005-09-10
Harleen,

Thanks for trying to help a NOOB!

Tried all your suggestions.  when I did the "find", the command "took" but came back with nothing.  also, when I used the file search in Unbuntu....nothing.

Why is this so difficult I wonder?

I did an "sh" command with a *.run file and it ran ok.

why such difficulty with an *.sh file?

I really want to learn how Ubunut works.

Thanks again.

---

### Post by mp3guy on 2005-09-11
[QUOTE=Statik]I'm doing the same thing, and I have no location yet. The command opens another terminal window that lists some stuff, but it closes before I can read it. How can I send that output either to the same window, or keep the other window open?

Statik[/QUOTE]

Yeah, i get the same thing, heres a screenshot

---

### Post by mp3guy on 2005-09-11
Wait, i found the solution

[http://www.ubuntuforums.org/showpost.php?p=322717&postcount=3](http://www.ubuntuforums.org/showpost.php?p=322717&postcount=3)

maybe it should be stickied?

Also, if q3demo then won't start, you've to put libGL.so in the directory you installed the game in.

And if sound doesn't work, do this
```

sudo chmod 777 /proc/asound/card0/pcm0p/oss
echo "q3demo.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

```

Then run q3demo

---

### Post by Alacrity on 2005-09-11
Thanks, MP3Guy for that piece of detective work!  If this is the "Gaming on Hoary 5.04"...which it is....and Q3 is new and popular software.....seems like this should be a sticky.

I have been revisiting Linux after a two year hiatus and was just about to conclude I had another two years to wait before Linux was ready to try once again.  At least this seems Q3 installer specific and not a Linux general issue.   Although, please forgive me but wow....  seems awful convoluted.  Ubuntu was such a pleasure to install too.  Maybe what they say on some of the forums is correct.....use Windows for gaming.  Seems to be a lot of "sound" challenges as well with Linux in gaming.  I ended up with solution #32 and used synaptic install for polyaudio.  Does that sound consumer ready?  Ubuntu and Linux seem more than solid for email, web surfing, and document exchanging.  But gaming...?  

Am I coming to the wrong conclusion here....or is Linux not yet there in the gaming department?

---

### Post by LeDechaine on 2008-02-08
Well.. hmm.. does this demo still works in Ubuntu 7.10 ?

Tried sudo sh (file) -target /tmp/q3 (or something ;)), the window opened, lines of info, then told me that "the installer closed normally", but without opening any other window, without asking me anything, and doing **updatedb** then **locate q3a**, **locate quake**, or even **locate q3** doesn't find anything related to the quake 3 arena demo.

So i'm guessing the demo hasn't even installed... 
So, like i said, this demo works in Ubuntu 7.10? And if yes, how can i install it? :)

---

### Post by LeDechaine on 2008-02-09
Also, by looking at /tmp/q3 i can see that there *is* install files there.. and a little setup.sh file that, when i try to execute it, tells me that "9" is an unknown command or something like that. *scratches head*

*deleting the tmp/q3 directory*

---

### Post by Sockerdrickan on 2008-02-09
Wow what a bump haha :KS
You would have to patch the sh file to be able to install as it should!

---

### Post by LeDechaine on 2008-02-09
Hmm? *scratches head*

(Agreed, woke up a 2 year old thread :P)

---

### Post by s_raiguel on 2008-06-01
Partly using tips offered here, I was able to get the  linuxq3..gz.sh to run, unpacking the initial quake 3 setup files, and then chowning and chmoding everything so that I have user-level access. When I try to run the extracted setup script, setup.sh, however, it runs up to line 9 then exits with
./setup.sh: 9: function: not found
x86
Now, I'm about one knowledge level above raw noob here. I know about about script files, but not enough about script language to know why it's bombing at this point. Has anybody found a patch or workaround, or have a modified setup.sh that will install quake 3 in Ubuntu from the extracted setup files? That failing, is there a way to hand-install the program, bypassing the script?

---

### Post by LeDechaine on 2008-07-07
Found the answer on another forum, i think you need to do "sh setup.sh" or "bash setup.sh", which means using the "old shell". Worked #1 for me.

---


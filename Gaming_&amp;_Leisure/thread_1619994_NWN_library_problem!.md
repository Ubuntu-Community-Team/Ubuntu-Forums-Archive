---
title: "NWN library problem!"
date: 2010-11-12
forum: Gaming &amp; Leisure
---

### Post by 10Digits on 2010-11-12
Hi,
I know this has been talked about a lot in the forums, but i cant seem to get any answers that would solve my problem.
whenever I try to run my ravage installer script my terminal gives me this output....

 sudo ./nwn_129_final.run 
[sudo] password for sayan: 
Verifying archive integrity... All good.
Uncompressing Neverwinter Nights 1.29 for Linux...............................................................................
/home/sayan/.setup5355: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


now I have done a search and came across to this thread with the same problem..[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=310286&page=2](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=310286&page=2)

but the solution doesnt work. I cant find the libgtk1.2 anywhere!!!
Can you tell me how I can fix this ??? Thanks!

---

### Post by Perfect Storm on 2010-11-12
You can search for it in previous ubuntu releases: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by 10Digits on 2010-11-12
Ok firstly thank you AI...I looked in there and tried snooping around in the forums and found this...[http://ubuntuforums.org/showthread.php?t=1502266](http://ubuntuforums.org/showthread.php?t=1502266)

I have successfully installed libgtk1.2 on my system and the ravager installer is running!

but for some reason its not accepting my DVD and is asking for my cd 2....

What do I do now?? :confused:
I am so close I can almost taste it!!!
Thanks in advance!

---

### Post by Perfect Storm on 2010-11-12
I use this guide: [http://gwos.org/doku.php/guides:64bit:nwn](http://gwos.org/doku.php/guides:64bit:nwn)
But there should be a guide on the forums with DVD version.

---

### Post by 10Digits on 2010-11-12
thank you AI..I have a feeling that this has not been the first time someone has come up to you regarding this!:)

I wanted to ask you a question...in the part where I use "nano nwn", I was unable to save it as nwn and I was forced to save it as Nwn...my question was if this changes anything or not?because my limited exposure with linux has taught me it is extremely case sensitive.

Also, the game was able to run but there was no sound, movies or text and it hung up the computer after I selected to make a character!
Can you tell me why???

Sorry if i am bothering everybody too much!

thank you for your patience!:)

---

### Post by Perfect Storm on 2010-11-13
Yes, Linux is case sensitive. I don't think it will any impact in this case, because it's the launcher script.

No sound, it may be because NWN is an old game that uses the old obsolete oss sound engine, you can try running the game with **padsp**. AFAIK in the next version of Ubuntu there will be a sound plugin (ossp) that will "translate" games/apps that uses oss.

NOTE: Games/Apps that write directly into the oss memory can't use the padsp workaround.
Another option, but an advanced one, is to build your own kernel and enable oss.

NWN linux there's no movie by default. There's a thread somewhere on the forums about bink player which nwn uses to get the movies to work - Though it never worked for me.


Hung up? Try launch the game through the terminal and see what it say, also check the error log of NWN (in nwn's directory).

---

### Post by 10Digits on 2010-11-13
Thank you again AI!!!!
I checked in the error logs and tried it from the terminal....no avail!!!
I can make do without the sound or movies but I atleast need the text to play the game...also for some ungodly reason its asking for my cd key everytime I start the game!!!

I guess I will wait for Natty ...and hopefully  there wont be any problems like this there!

keeping my fingers crossed!
and thank you once again!

---


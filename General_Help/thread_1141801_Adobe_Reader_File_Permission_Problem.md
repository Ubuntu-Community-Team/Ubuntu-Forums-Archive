---
title: "Adobe Reader File Permission Problem"
date: 2009-04-28
forum: General Help
---

### Post by bob-linux-user on 2009-04-28
I Installed Adobe Reader For Linux 9.1.0 on Ubuntu Jaunty. When I try to save a copy of a pdf I get the following message:
"you do not have permission to write to this file"
Everything else seems to be running ok
Has anyone else had this problem/got any ideas please?

---

### Post by _Purple_ on 2009-04-28
Can you post the exact error message? Does it say file or folder?

---

### Post by bob-linux-user on 2009-04-28
Hello Purple.
Thanks for your prompt response. It says file-exactly as I had it before.
Regards
Bob

---

### Post by _Purple_ on 2009-04-28
Hello Bob,
Do you have permission to write in the folder you are trying to save the file in? In which folder did you try to save it?

---

### Post by bob-linux-user on 2009-04-28
Hello Purple
Yes it is a FAT 32 partition where I store all my documents (I dual boot with XP when I have the patience to watch XP boot up) I save stuff in there all the time.

---

### Post by _Purple_ on 2009-04-28
Hello Bob,
Why don't you try Evince (Document Viewer)?

---

### Post by bob-linux-user on 2009-04-28
Yes I have tried Evince-I think it is installed by default. I had always guessed that Adobe Reader gave a better picture.To my complete surprise,now that you have "made me" try it, on the same PDF, Evince gave a better picture.

I used Adobe as I quite familiar with it- I have to use the Windows version at work.

I will carry on with Evince but I am still curious as to what the problem is. Will log on again Wednesday evening. Thanks

---

### Post by _Purple_ on 2009-04-29
I use evince even though I have Adobe Reader 8 installed in my PC. I can save files in my FAT32 or NTFS partitions using Adobe reader. I am not sure what is causing this problem or if it is specific to version 9.1 only. You can open it using 
```
gksudo acroread
```  

That will open Adobe Reader with root permission.

---

### Post by bob-linux-user on 2009-04-29
Hello Purple. I think you are right -it is a problem with version 9. I removed it and installed version 8 which has worked ok in the past. In the future though I think I will just use evince.Thanks for your help.

---

### Post by MontelEdwards on 2009-04-29
> **bob-linux-user said:**
> Hello Purple. I think you are right -it is a problem with version 9. I removed it and installed version 8 which has worked ok in the past. In the future though I think I will just use evince.Thanks for your help.
If you are getting a permission error, run it as root.
just press alt and F4 or F2, i forgot which one. and enter
```
gksudo nautilus
``` and then go to where you have to file saved in, this will work around the permission error. also, to get permanent access to it, i would right click on the file, click on permissions, and then change the owner to your username

---

### Post by _Purple_ on 2009-04-30
> **bob-linux-user said:**
> Hello Purple. I think you are right -it is a problem with version 9. I removed it and installed version 8 which has worked ok in the past. In the future though I think I will just use evince.Thanks for your help.


Hello Bob, 
I installed acroread 9.1 and the same thing happens. I am not sure if this is a bug. May be someone else can confirm.

---

### Post by Zeedok on 2009-05-05
I've just noticed this problem as well.  I also installed Adobe Reader 9.1 when I upgraded to Jaunty.  It seems only to be a problem with certain directories - for instance, I can save from Adobe Reader to the Desktop, but not my preferred directory.  Using other programs (including Evince) I can save to my preferred directory no problems.  

Is it possible to assign permissions or group access to adobe reader??

PS - I would love to use Evince as my primary document reader, but I prefer to read my pdfs in Firefox - if anyone knows of a Evince pdf plugin I'd definitely switch . . .

---

### Post by Zeedok on 2009-05-05
I'm not sure if it is a bug., but it is definitely Acro Reader 9 specific - I have just reverted to 8.1 and all is well . . .

---

### Post by MontelEdwards on 2009-05-05
uh, i have never had this problem.
how did you install Adobe reader?


well i downloaded the .bin off their website.
remove what you have now, and call this command
```
wget http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.1/enu/AdbeRdr9.1.0-1_i486linux_enu.bin
sudo chmod a+x AdbeRdr9.1.0-1_i486linux_enu.bin
sudo ./AdbeRdr9.1.0-1_i486linux_enu.bin
```



of course...
applications> accessories >terminal

---

### Post by wahlau on 2009-05-12
But this does not really make sense - why can Adobe Reader 9.1 write to some partitions (using Ext3) and not to a VFAT/FAT32 partition? 

i actually tried changing the umask to 000, so that all can write but it still does not work.

---

### Post by pendlaren on 2009-05-29
> **MontelEdwards said:**
> uh, i have never had this problem.
how did you install Adobe reader?


well i downloaded the .bin off their website.
remove what you have now, and call this command
```
wget http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.1/enu/AdbeRdr9.1.0-1_i486linux_enu.bin
sudo chmod a+x AdbeRdr9.1.0-1_i486linux_enu.bin
sudo ./AdbeRdr9.1.0-1_i486linux_enu.bin
```


I also had this problem, so I removed the aptitude package and followed your recipe, but the same strange result occured.
Uninstalled it and installed from .deb-file of 8.10 from [http://get.adobe.com/uk/reader/otherversions/](http://get.adobe.com/uk/reader/otherversions/), and that works well.

---

### Post by dugh on 2009-08-17
I see the same issue when trying to save to an NTFS drive - has anyone filed a bug report?

I reported this issue here: [https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/414862](https://bugs.launchpad.net/ubuntu/+source/acroread/+bug/414862)

---

### Post by mental_u on 2009-10-28
i am also having exactly the same problems reported above: abode reader 9.2.  is there a way to change the write permission of adobe reader itself (assuming this is the problem) without opening it using terminal (i.e. if firefox calls it)?

---

### Post by panache on 2010-03-30
still no solution to this problem?

---

### Post by MontelEdwards on 2010-03-31
I am just curious..
Why are you guys using Adobe Reader? Evince works great and is OSS

---

### Post by bob-linux-user on 2010-05-31
@Montel Edwards..

Well, in answer to your question, as I dual boot with Windows I find it easier to use Adobe Reader on both setups. Also I am very used to Adobe because I use the "full monty version" every day at work. I know it is not OSS though.

---

### Post by kiers on 2010-08-28
INteresting! I have Ubuntu Netbook Edition 10.04 on my netbook and Win xp on desktop. i have a shared folder on my windows machine through which i can access files from the netbook using ubuntu samba. 

However, some PDFs ARE able to be opened by Evince reader, and some are NOT! it complains about permission denied! wtf?

evince SHOULD be able to read everything?

any ideas? the sharing is working cause some pdfs are being opened in ubuntu! so it's not samba related.

I don't even have acrobat installed on my Ubuntu system. No use for it. however acrobat 9.0 IS installed on the desktop and IT manages to open  everything fine on the desktop.

---


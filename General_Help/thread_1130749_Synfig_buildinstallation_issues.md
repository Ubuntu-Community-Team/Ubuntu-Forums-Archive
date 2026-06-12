---
title: "Synfig build/installation issues"
date: 2009-04-20
forum: General Help
---

### Post by David C. on 2009-04-20
Okay, experiencing some issues here with the install. I've read through the posting [**How to build Synfig in Ubuntu Intrepid 8.10**]("http://synfig.org/forums/viewtopic.php?f=13&t=277"),followed the first two instruction lines:

$sudo apt-get install build-essential

then:

$sudo apt-get remove libsynfig0

No problems there. 

Then, I downloaded the files, saving to my Desktop first. Entered the  statement, as per Synfig's isntructions:

$tar -xvzf ETL-0.04.12.tar.gz

And received this error:

tar: ETL-0.04.12.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

So, I changed the directory from home to desktop and tried again...same error. 

I read through various posts here and followed the instructions that are posted in this thread: [**I need help kind of bad**]("http://ubuntuforums.org/showthread.php?t=972446&highlight=synfig") and created a "Source" folder in Home and extracted all three files to that folder. Entered the first line of code: 

$sudo apt-get build-dep synfigstudio

That worked, but when I entered the next line:

cd ETL-0.04.12

I get this: 

bash: cd: ETL-0.04.12: No such file or directory

Yet, ETL is located in the same Source folder as synfigstudio and synfig. 

What am doing wrong and how do I correct the error? FYI- I'm new to Ubuntu/Linux and to shell scripting, so bear with me, as I am not familiar with the jargon or the code syntax.

---

### Post by jayjay960 on 2009-04-20
Are you in the synfig source folder already? If not, do:

cd /path/to/source/folder/ETL-0.04.12

(Of course replacing /path/to/source/folder with the actual path)

---

### Post by David C. on 2009-04-21
No. Still getting the error:

bash: cd: /path/to/source/folder/ET-0.04.12: No such file or directory

I checked the location of the file folder Source in its properties and the location listed is /home/jdc

I entered **cd /home/jdc/source** and received the error: bash: cd: /home/jdc/source: No such file or directory

The file is physically there, but I can't figure out why the system is unable to find ETL-0.04.12 in the source folder or locate the folder. It located the folder synfigstudio, when I entered:

$sudo apt-get build-dep synfigstudio

And synfigstudio is in the same Source folder as ETL. 

The path is the same, unless the system grabbed synfigstudio from the older version that came installed w/Ubuntu. But, I don't know how to double check this. libsynfig0 was removed, which if I understand the syntax is the library, don't know if removing that removes everything associated with the application. Synfig 0.06.08 and its associated files still show in the Synaptic Package Manager, but are not installed. 

I've tried to copy and paste the source folder into the file browser and into the home folder, but the system doesn't allow it. The paste is "grayed" out. Of course, the permissions aren't there when I checked the properties, and I'm not sure how to change that with "root" and do it correctly or if its really necessary.

---

### Post by David C. on 2009-04-21
Bumping...still in need of some assistance with this. 

thanks.

---

### Post by AnimalCrosser5 on 2009-04-29
If you still need help, this worked for me:
[http://www.onyrix.com/computer-science/ubuntu/how-to-install-synfig-on-ubuntu-810/comment-page-1#comment-33809](http://www.onyrix.com/computer-science/ubuntu/how-to-install-synfig-on-ubuntu-810/comment-page-1#comment-33809)

---

### Post by David C. on 2009-04-30
Thanks, I'll take a look.

---

### Post by Puzzlenoise on 2009-05-14
It doesn't work like I want it to. I installed Synfigstudio, but still - there are some issues. I can't see the icons... here a screen:
[URL="http://img207.imageshack.us/img207/1917/screenshotfft.png"]
[IMG]http://img207.imageshack.us/img207/1917/screenshotfft.th.png[/IMG][/URL]

How can I solve this problem?

---

### Post by BCtom on 2009-05-16
> **Puzzlenoise said:**
> It doesn't work like I want it to. I installed Synfigstudio, but still - there are some issues. I can't see the icons... here a screen:

How can I solve this problem?

Puzzlenoise, 

This may help--it worked for me. Well, at least it got my icons back. This is from the Synfig forum:

 [http://www.synfig.org/forums/viewtopic.php?f=13&t=277&st=0&sk=t&sd=a](http://www.synfig.org/forums/viewtopic.php?f=13&t=277&st=0&sk=t&sd=a)

I hope that helps you out. I know it is a lot work, but rebuilding it gets it running the way it is suppose to--and the instructions are good--I think? Perhaps the next Ubuntu Build will synk everything up properly.

---


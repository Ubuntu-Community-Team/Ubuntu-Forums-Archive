---
title: "How to run Cisco CCNA exploration in Ubuntu"
date: 2010-06-14
forum: Education &amp; Science
---

### Post by A_M_S on 2010-06-14
Hi.

I can't run th cisco ccna exploration course on Ubuntu.

I've downloaded the documentation locally and after the opening page (present in the image attachment )e can't enter in any chapter.


The problem persists in different browsers (firefox, chrome, epiphany) 

It seems to be a flash issue. 

Any ideas?

Tnx.

---

### Post by earache on 2010-09-05
file:///media/win/CISCO_CCNA/Exploration3_English/theme/cheetah.html?cid=1300000000&l1=en&l2=none&chapter=2

I start it in this fashion... points to chapter 2 in expl 3.

---

### Post by Wistful on 2010-09-07
Cisco documentation requires [Flash player]("http://get.adobe.com/flashplayer/") to properly work. If you have it installed - correctly - it should work! Also try using Firefox instead of Chrome when reading the documentation.

---

### Post by A_M_S on 2010-09-08
Thank you for the replies.


I've already found the issue.


You have to access the global settings of flash player (right click on the flash image in the exploration index file)

Clink on the "Global Security Settings panel" link

Click on add location

Add the complete path to your local site.

You can see a partial screenshot of the "Global Security Settings panel" in the attachment.

---

### Post by rabah-katib on 2011-01-29
thank you very much

---

### Post by dio3 on 2011-04-10
Thank you!

---

### Post by mnemonict on 2011-04-11
Sorry, but I never see like this... How to do this??
I use Chrome browser and version of my flash player is 10.2.154.8....

Thanks

> **A_M_S said:**
> Thank you for the replies.


I've already found the issue.


You have to access the global settings of flash player (right click on the flash image in the exploration index file)

Clink on the "Global Security Settings panel" link

Click on add location

Add the complete path to your local site.

You can see a partial screenshot of the "Global Security Settings panel" in the attachment.

---

### Post by mnemonict on 2011-04-11
Can you explain us, about this thing?

thanks

> **earache said:**
> file:///media/win/CISCO_CCNA/Exploration3_English/theme/cheetah.html?cid=1300000000&l1=en&l2=none&chapter=2

I start it in this fashion... points to chapter 2 in expl 3.

---

### Post by mnemonict on 2011-04-15
Here is Mine :

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration1/theme/cheetah.html?c1lang=en&c1id=en0600000000&c2lang=&c2id=&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration2/theme/cheetah.html?c1lang=en&c1id=en0900000000&c2lang=&c2id=&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration3_English/theme/cheetah.html?cid=1300000000&l1=en&l2=none&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration4_English/theme/cheetah.html?cid=1400000000&l1=en&l2=none&chapter=1

Change 0430C6B030C6A7CE with the CCNA's Installation folder, but read from linux... 

hope this help. :)

---

### Post by supergroove00 on 2011-05-21
hi there, 
can someone tell me where to find course material to downlaod
thanks

---

### Post by Sef on 2011-05-22
> hi there, 
can someone tell me where to find course material to downlaod
thanks

You have to buy the course material. Downloading it would would be illegal since it is copyrighted, (unless you pay for it), and therefore a violation of the Ubuntu Code of Conduct, so please do not ask again.  Thank you.

---

### Post by supergroove00 on 2011-05-22
i didnt know that mate.i thought since packet tracer is free for download course material would be as well.
thanks for reply

---

### Post by kigathi_wanyeki on 2011-06-26
thanks A_M_S

---

### Post by KaPePinG on 2011-08-08
hi .. i tried all the instructions.. but the button isn't functioning at all.. 

my installer in ccna is from windows..meaning its an .exe format.. i use wine so that i can install it on linux.. and i tried all the solution.. using flash global something someone mentioned it awhile ago.. 


arggg.. im stuck at this.. help me..

---

### Post by JosephWheatley on 2011-10-18
I got the Cisco CCNA exploration exe files installed and working on my Ubuntu 11.10 Eee PC.

First Wine is needed. I installed wine 1.3 from the Ubuntu Software Centre.

Then to install the exploration material click on the exe as wine will associate with it. If it hasn't and Archive Manager tries to open it right-click on the exe file and choose 

**Open with -> Wine Windows Program Loader**

Wine will install it to the hidden .wine folder in your home folder.

You can access it by opening the home folder and pressing **ctrl-h** to show hidden files. Then navigate to the Cisco folder

**~/.wine/drive-c/CISCO-CCNA**

In here you will see the folders of the installed material e.g. /Exploration1_English

In this sub-folder click on index.html

It will open in Firefox. At this point you will find the button "Launch Course" won't respond.

So you need to go to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html) and check ***Always Allow***. 

You then need to add the location of the Cisco Exploration files to the trusted files list.
From the drop-down list click on **Add location** and paste in the address of the Cisco folder.

e.g. **/home/joseph/.wine/drive_c/CISCO_CCNA** -add you user name to this address

Click on confirm and refresh the page to check that the change has stuck and it is still checked as ***Always Allow***

Now when you choose a chapter from the list on the Exploration Index page it will open in a other window.

Job Done

---

### Post by til on 2011-10-22
Thanks A_M_S!

---

### Post by kon_kon on 2011-11-23
> **A_M_S said:**
> Thank you for the replies.


I've already found the issue.


You have to access the global settings of flash player (right click on the flash image in the exploration index file)

Clink on the "Global Security Settings panel" link

Click on add location

Add the complete path to your local site.

You can see a partial screenshot of the "Global Security Settings panel" in the attachment.

worked for me

thanks mate

---

### Post by aneez004 on 2012-01-02
Thanks man
That was awesome
But why adobe store our location????????

---

### Post by Melinium on 2012-02-08
> **JosephWheatley said:**
> I got the Cisco CCNA exploration exe files installed and working on my Ubuntu 11.10 Eee PC.

First Wine is needed. I installed wine 1.3 from the Ubuntu Software Centre.

Then to install the exploration material click on the exe as wine will associate with it. If it hasn't and Archive Manager tries to open it right-click on the exe file and choose 

**Open with -> Wine Windows Program Loader**

Wine will install it to the hidden .wine folder in your home folder.

You can access it by opening the home folder and pressing **ctrl-h** to show hidden files. Then navigate to the Cisco folder

**~/.wine/drive-c/CISCO-CCNA**

In here you will see the folders of the installed material e.g. /Exploration1_English

In this sub-folder click on index.html

It will open in Firefox. At this point you will find the button "Launch Course" won't respond.

So you need to go to [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html) and check ***Always Allow***. 

You then need to add the location of the Cisco Exploration files to the trusted files list.
From the drop-down list click on **Add location** and paste in the address of the Cisco folder.

e.g. **/home/joseph/.wine/drive_c/CISCO_CCNA** -add you user name to this address

Click on confirm and refresh the page to check that the change has stuck and it is still checked as ***Always Allow***

Now when you choose a chapter from the list on the Exploration Index page it will open in a other window.

Job Done

thanks bro it works good now ;)

---

### Post by leonavas2185 on 2012-03-11
Hi, I have Ubuntu 11.10 installed and I have exactly the same issue, the only problem is that I cant see any Global Security Settings panel when I right right click on the exploration index file, I have installed Flash player from Ubuntu software center, any ideas on what could be the problem???

---

### Post by leonavas2185 on 2012-03-11
Hello guys I found al alternative Solution after some research for some reason after I installed Flash player from Ubuntu Software center firefox used Gnash instead of flash player so I downloaded install_flash_player_11_linux.i386.tar.gz 

to install it just open terminal and do the following commands

tar zxvf install_flash_player_11_linux.i386.tar.gz  
[FONT=monospace]then
[/FONT]sudo cp libflashplayer.so /usr/lib/mozilla/plugins

now you just copied the files to firefox, that resolved the issue for me since I couldnt see the online content from cisco academy

original post in 
[http://ubuntuforums.org/showthread.php?t=1859842&page=2](http://ubuntuforums.org/showthread.php?t=1859842&page=2)

---

### Post by denzify on 2012-11-09
this one worked for me... thanks....

---

### Post by levonh on 2013-07-19
Hi all,
For launching CCNA on any type of linux distribution the best way to install apache 
and put CCNA into /var/www and there is no any issue regarding flash player:)

---

### Post by zvonko2 on 2013-09-23
> **mnemonict said:**
> Here is Mine :

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration1/theme/cheetah.html?c1lang=en&c1id=en0600000000&c2lang=&c2id=&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration2/theme/cheetah.html?c1lang=en&c1id=en0900000000&c2lang=&c2id=&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration3_English/theme/cheetah.html?cid=1300000000&l1=en&l2=none&chapter=1

file:///media/0430C6B030C6A7CE/CISCO_CCNA/Exploration4_English/theme/cheetah.html?cid=1400000000&l1=en&l2=none&chapter=1

Change 0430C6B030C6A7CE with the CCNA's Installation folder, but read from linux... 

hope this help. :)

Hi, 
this really helped me and saved me from further searching for solution. I was trying to run CCNA Explration on Android tablet and I could not make it to lunch properly by opening index.html in Firefox. Then I saw this hint, tried and it works without problems! Only difference is, like you said,  that I have to put correct path to cheetah.html into the address  bar of Firefox. Finally, I created new index.html that refers to this new path and I can run my Exploratoin on Android, at last :)

Zvonko.

---

### Post by marcohnunez2 on 2014-07-16
Hi Everybody,

I got this problem again, but on KDE4 (Kubuntu 14.04) the link ([http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html)) privided by [**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=994378")**JosephWheatley**, gave me the solution I've been looking for a couple of days, thanks bro
and don't forget to refresh the CCNA front page on firefox

---

### Post by earl8 on 2015-03-07
worked great for me! thanks! :)

---

### Post by bellasnaru on 2015-03-17
im having alot of trouble getting CCNA to work from the website, i go to netacad, login, launch the course and it doesnt work

i've tried every flash method in this thread accept global settings

i cant seem to figure out with firefox and unity how to get to the global flashplayer settings

---


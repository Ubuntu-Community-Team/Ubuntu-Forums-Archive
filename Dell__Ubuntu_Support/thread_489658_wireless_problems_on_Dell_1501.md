---
title: "wireless problems on Dell 1501"
date: 2007-07-01
forum: Dell  Ubuntu Support
---

### Post by daveo2050 on 2007-07-01
The only thing keeping Vista on my laptop is my lack of wireless capabilities with Feisty.

I have followed the instructions at the link below to set up *ndiswrapper* 1.42.

[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)

At *install the driver and restart again* portion of the instructions, I type "sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf", my terminal says 'driver bcmwl5 is already installed'.

I then paste "sudo ndiswrapper -l", my terminal says the driver is invalid.

What else can be done to activate my wireless?

---

### Post by Unicast on 2007-07-01
That should work, but I followed the referenced guide: [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html](http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html)

I used ndiswrapped 1.47 and the latest XP driver 151517.exe off the Dell site.

I promise you it does work!

---

### Post by ross350 on 2007-07-04
[SIZE="3"][COLOR="Red"][B]]doesn't WORK!!

I've tried sooo many times i got the same thing as the guy who started this everything seems to work 
but in the end nothing is actually installed at all!!
am i doing it the wrong place should i do this entire guide in root. i did it and saved both downloads to a file named .driver(wich i created ) (is there supposed to be one in there allready?)
its a hidden file. anyway inside that folder i created another folder named wifi for my driver download (the zipped one) so after that i un TAR the ndiswrapper file to the .driver folder and do everything as the guide says, thousands of dell owners have. it doesn't work for me.
the guide seems to be a bare skeleton when it comes to the informative and descriptive side... 

getting no where and have reinstalled twice can you edit your guide a little, starting at the verry first line,,,,

after you suggest the root folder option you say to enter the 2 previous command's again....

which 2? the first 2 in the guide or the one to become root . there are some other confusing factors too. it seems to work for some people but i am having trouble. 

and your guide for the beryl thing dont get me started....

you should tell people what it means to log in as XGL  no everyone knows its a profile.. i can proof read your guides to make them idiot proof , I am half idiot after all... [/B][/COLOR][/SIZE]

---

### Post by sj3fk3 on 2007-07-04
> **daveo2050 said:**
> The only thing keeping Vista on my laptop is my lack of wireless capabilities with Feisty.

I have followed the instructions at the link below to set up *ndiswrapper* 1.42.

[https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29](https://help.ubuntu.com/community/WifiDocs/Driver/1390?highlight=%28WifiDocs%2FDriver%29)

At *install the driver and restart again* portion of the instructions, I type "sudo ndiswrapper -i ~/.driver/wifi/DRIVER/bcmwl5.inf", my terminal says 'driver bcmwl5 is already installed'.

I then paste "sudo ndiswrapper -l", my terminal says the driver is invalid.

What else can be done to activate my wireless?

The output is right. If I'm not mistaken Feisty has out of the box support for broadcom wireless card, you do need firmware cutter to get that little piece of binary firmware. Have a look at [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174) n.b. it's always good to search the forum before you post a question. 80% of the questions are faq's

Then again.. 99.34% of all statistics are made up.

---

### Post by Dewni on 2007-07-04
> That should work, but I followed the referenced guide: [http://ubuntu1501.blogspot.com/2007/...dell-1501.html](http://ubuntu1501.blogspot.com/2007/...dell-1501.html)

I used ndiswrapped 1.47 and the latest XP driver 151517.exe off the Dell site.

I promise you it does work

Worked for me as well. The thing is, the 1501 wireless card is recognized correctly, bcm43xx module is loaded and indeed only needs the firmware. So it is not working out of the box, but very nearly so. There are probably copyright reasons why Ubuntu cannot be shipped with the firmware to get this working out of the box.

I used the guide quoted above to get my wireless working in the 54Mbit mode, this currently doesn't work in the bcm43xx drivers although you can set an option to use 54mbit mode. Using ndiswrapper solved the problem for me and provided me with a nice 54mbit connection.

One small remark to ross350: most of these things happen because our friends at Broadcom are not so helpful in providing details about their chips. If they would the bright minds in the linux community would have developed drivers already and wouldn't have you jumping through hoops to get it working. Patience, my friend!

---

### Post by Unicast on 2007-07-04
**ross350:** The guy whose blog I mentioned in my last post had updated his wireless guide to make it idiot proof.

It does work, honestly! ;)

---

### Post by pHreaksYcle on 2007-11-12
For everyones sanity, the Ubuntu on the 1501 blog stands and will most likely continue to stand until the 1501 is outdated. It moved to [http://www.ubuntu1501.com](http://www.ubuntu1501.com) recently and if you have any issues running Ubuntu on this specific laptop or perhaps a similar one, check this site out, most likely there is already an answer.

---

### Post by Dellfan on 2007-11-13
You also can look at the Dell wiki for info on how to use ndiswrapper to install Windows drivers... just make sure you are using the correct driver for your wireless card. The nice thing about this approach is that support.dell.com has all the current Windows drivers for Dell's wireless cards.

[http://http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper]("http://http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")

---


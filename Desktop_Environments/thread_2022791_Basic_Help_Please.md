---
title: "Basic Help Please"
date: 2012-07-11
forum: Desktop Environments
---

### Post by Chuckymong on 2012-07-11
Hey people, I recently posted on here about ubuntu desktop which I installed on an old machine I have. Well that failed epically so I went a researched about some other distrobutions and came across lubuntu which looks promising. I am completely new to the ubuntu operating systems therefore I`m seeking some advice about its functionality.

The thing I am asking is what featurers of lubuntu are available for use if I list some of the things I am looking for.

Primarily I would like some form of AMP setup, not nessersarily hosting to the web but internally  so I can use it as my programming machine although web hosting would be a bonus.

I am pretty sure that the JDK and JRE should be available but there is no harm in asking for confirmation of this.

Which if any browsers are compatable with lubuntu for testing website cross browser compatability.

I`m not entirely sure but I figured for example if I wanted to download a program, if a linux download link is available, I should use that, otherwise I should leave it or seek some form of emulation.

I am sincerley sorry if any of those seem almost "stupid" questions but i would rather have some clarification before I go diving in. Other than that I am looking forward to joining the ubuntu OS community.

Thanks for any help - Marcus.

---

### Post by papibe on 2012-07-11
Hi Chuckymong. Welcome back!

For a web server I would choose Ubuntu Server Edition. It would give you the best performance, because there's no resources dedicated to the GUI.

Having said that, if you are going to work on the server itself as a workstation, then it would be nice to have a GUI.

As for browsers, Lubuntu uses Chromium by default, but as in any other desktop environment, you can install as may browsers as you want.

I hope that points you in the right direction.
Come here often and have fun.
Regards.

---

### Post by madjr on 2012-07-11
this might clarify:

[http://psychocats.net/ubuntu/whichbuntu](http://psychocats.net/ubuntu/whichbuntu)

---

### Post by Chuckymong on 2012-07-11
First of all thanks for the speedy reply. I have used ubuntu sever once a long time ago. I think I had it installed for a day, then an unfortunate event meant I had to get rid of the laptop I was running it on. Thank you for clarifying everything for me I just have one more issue that I forgot to state in my first post. It needs to be very lightweight as the computer is very low spec (1.7GHz, 50GB storage and only 1GB RAM). Another important requirement I forgot to mention is that it needs to have a GUI as my partner will be using it for nothing more than browsing the web and possibly some general documentation a.g. Letters etc.

Thanks again for any advice - Marcus.

EDIT: Fixed spelling mistakes, I apologise for any inconvienience I am using my phone.

---

### Post by Chuckymong on 2012-07-11
> **madjr said:**
> this might clarify:

[http://psychocats.net/ubuntu/whichbuntu](http://psychocats.net/ubuntu/whichbuntu)

Thank you for the reply. I will be sure to have a read through in a moment.

Thanks again - Marcus.

---

### Post by Mr.Dee on 2012-07-11
What was the unfortunate event that made you give up your laptop?

---

### Post by Chuckymong on 2012-07-11
> **Mr.Dee said:**
> What was the unfortunate event that made you give up your laptop?

Without being disrespectfull or rude I dont think that it makes any difference to my question therefore would rather keep it private but thank you for reading.

My apologies if this comes across as blunt, that is not what I intended - Marcus.

---

### Post by Chuckymong on 2012-07-11
> **madjr said:**
> this might clarify:

[http://psychocats.net/ubuntu/whichbuntu](http://psychocats.net/ubuntu/whichbuntu)

I have had a quick read through and have noticed some good news that most of the programs I used on windows are compatable with linux therefore I do not have to worry about this anymore. Thank you for that resource I will have a more in depth read through it all later on.

Marcus.

---

### Post by Rodney9 on 2012-07-12
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by Cheesemill on 2012-07-12
> **Chuckymong said:**
> Primarily I would like some form of AMP setup, not nessersarily hosting to the web but internally so I can use it as my programming machine although web hosting would be a bonus.
You can install the LAMP stack on any version of Ubuntu. It's as easy as:
```
 
sudo apt-get install lamp-server^

``` 
> I am pretty sure that the JDK and JRE should be available but there is no harm in asking for confirmation of this.
The open source versions of Java are availible in the standard repositories.
If you need Oracle Java you can install it from the WebUpd8 PPA just by doing:
```
 
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

``` 
> Which if any browsers are compatable with lubuntu for testing website cross browser compatability.
Any of the programs that are available for Ubuntu can also be installed in Lubuntu.
The default Lubuntu browser is Chrome but you can easily install Firefox or any of the other browsers in the Software Center. 
> I`m not entirely sure but I figured for example if I wanted to download a program, if a linux download link is available, I should use that, otherwise I should leave it or seek some form of emulation.
Don't download software from websites, that's a Windows mindset.
All software should instead be installed from the Software Center.
There's a good introduction here for Ubuntu but exactly the same process works for Lubuntu as well.
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Chuckymong on 2012-07-12
Thanks peiple thats the exact kind of answer i was after. I have favourited these websites for future refference before posting on here.

Thanks for taking the time to help - Marcus.

---


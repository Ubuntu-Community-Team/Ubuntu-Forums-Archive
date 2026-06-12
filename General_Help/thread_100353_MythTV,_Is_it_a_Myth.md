---
title: "MythTV, Is it a Myth?"
date: 2005-12-07
forum: General Help
---

### Post by Micro Rotors on 2005-12-07
Hello All,

  I have been trying to install MythTV now for 2 days, now working on my 7th try. I am using a Win150 PVR On Breezy and have followed the the how to guide in the hints and tips section.  The problem is that the guide has flaws, quite a few in fact as far as I can see. I am a newbie at this so when I go to look at a how to I kind of expect it to be correct. I know the people involved have spent a ton of time writing this guide up, but as long as it has been up, I think that it should have been fixed by now. Like I said I am a newbie and I hope I am not stepping on any toes here and I hope that one would understand that I am a little frustrated at this point trying to set this up while trying to figure out this stuff at the same time.

First lets start with the how to guide.

The first line is this and know matter how I type this in, it says “event not found”. I have removed the    [ ]  brackets and put root  or my user name in were the 1. is and still no go.

[PHP]<!--[if !supportLists]-->1.      <!--[endif]-->Open up a terminal (Applications à System Tools à Root Terminal)[/PHP]

Now the next thing is the source list. They all have hoary in them.  Now if this was a guide for Hoary, well then they are fine but as the title says Breezy Badger, this is incorrect. These should be fixed now!

[PHP]deb http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary universe multiverse

deb-src http://us.archive.ubuntu.com/ubuntu hoary universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted

deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse

deb-src http://security.ubuntu.com/ubuntu hoary-security universe multiverse[/PHP]

Now we come to Phase Two, everything is good until you get to the part that asks for [PHP]HcwMakoA.ROM[/PHP] and it says that its on the CD that is included with the card. Well the CD that came with the card does not have that file on it. It has HcwMakoB.ROM and HcwMakoC.ROM but not HcwMakoA.ROM!

I had to google up a zip file named pvr_2.0.24.23035.zip and extract the HcwMakoA.ROM file from that.

Now the next one is back at supportLists, again, same problem as before with this.

[PHP]<!--[if !supportLists]-->1.      <!--[endif]-->type halt and run far, far away

<!--[if !supportLists]-->2.      <!--[endif]-->type whoami[/PHP]

Now the next one is the sudo line it work only if I leave the sudo part off and run it without it. 

[PHP]sudo cd ivtv-0.4.0/util[/PHP]

Now the next one is were you move some files 4 of them to be exact. Well the first one is wrong. First off the sudo is missing at the front of the first line and it says that the file is 2.6.10-5-386 and it should be 2.6.12.9-386 as are the other three.

[PHP] mv /lib/modules/2.6.10-5-386/kernel/drivers/media/video/msp3400.ko /lib/modules/2.6.10-5-386/kernel/drivers/media/video/msp3400.ko.original

sudo mv /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda9887.ko /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tda9887.ko.original

sudo mv /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tuner.ko /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tuner.ko.original

sudo mv /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tveeprom.ko  /lib/modules/2.6.12-9-386/kernel/drivers/media/video/tveeprom.ko.original[/PHP]

Now the next one is were you are supposed to put the modules to were you can use them. The file name is stretched apart but one can see that and adjust it.

[PHP]sudo cp /lib/modules/2.6.12/ivtv/* /lib/modules/2.6.12-9-          386/kernel/drivers/media/video[/PHP]

Now I have followed the steps so far I believe but now when I type dmesg I get an error that says it cannot find the ivtv modules.
Now this is were I give up. I just cant go any further and I dont know whats installed correctly and whats not, This is the first thing I have installed on this box as I want it to be my freevo machine si I have reinstalled Ubuntu six times now and I will be giving up on this seventh if I cant get any information on how to do this correctly. I also need to find out if what I have done so far is correct or not.

Like I said before, the people who have done this write up have spent a great deal of time doing so, but as it is now, To me its a great waste of time on thier part to write this up, and on mine also in trying to set up what cannot be set up like this and will surely turn some future Linux wannabes into hard core Gates mortgage payers.

Please do not give us a 2005 chevy manual and tell us about 1994 parts and ford rearends.

Sorry if it sounds like I am complaining,,, well I am, but its with cause.

---

### Post by thespazzz on 2005-12-07
I never could get the default install for Myth TV to work.  There is a Knoppix Myth CD I had a little more luck with, Still nothing that worked but I blame that more on my cobbled togeather harware I was using at the time.  After christmass I plan on trying agian with hardware I know s Linux compatable.

---

### Post by quietglow on 2005-12-07
Great points for discussion here! I'll be happy to take each in turn.

 > I am a newbie at this so when I go to look at a how to I kind of expect it to be correct. 

This sort of expectation will not, I'm afraid, get you very far in the world of Linux. We all do the work we can and get things as good as possible in the time we can allot. Things don't work a whole lot of the time. Part of the fun is in figuring them out!


> I think that it should have been fixed by now. 

I actually have been spending my time dedicated to OSS stuff for the past several weeks helping a local school get Edubuntu up and running on a few computers they got with a federal grant. Making sure everything works properly on the MythTV (and by extension your PVR) howto is (and will be!) a much lower priority. 

> I hope that one would understand that I am a little frustrated at this point trying to set this up while trying to figure out this stuff at the same time.


I understand how you can be frustrated. You should also understand you and only you can make your computer work the way you want it to. You can ask for help, follow howto's--whatever helps you out. But we are buddies in your computer quest--not business associates. When we're playing with linux and our stuff doesn't work, we try to figure out why. And when we do, we let others know how we did it! Which brings me to my next point:


> To me its a great waste of time on thier part to write this up, and on mine also in trying to set up what cannot be set up like this 

Nope it sure isn't. I followed those directions and kept a running log and got a working MythBox. My running log wasn't perfect, but it got at least a couple of other people through the process. 

I'm sure the original author would agree with me when I say that if you think the document needs improvement, by all means have at it! Lets solve your problems and then you can do the next rewrite and we'll go from there. 

So, we'll start with problem #1: the first line you are typing in isn't a command. Its a suggestion that you open up a terminal. I'm not sure what the brackets are that you're referencing. So get that terminal open, sudo that gedit and we'll go from there.

---

### Post by factotum218 on 2005-12-08
[QUOTE=quietglow] Lets solve your problems and then you can do the next rewrite and we'll go from there. [/QUOTE]


You could have summed up your entire post with that one sentance minus the Edubuntu gloating. I also do volenteer work with low-income people to get computers usually with Linux or BSD whenever possible. Yes me, that pic of that freak on my avatar. Even I can play the good guy when it comes to something like computers and the people around me. Problem is, people dont realize how easy it is to do this sort of thing once they gain knowledge from people more experienced then they themselves are.
As you can tell I don't have an answer either, now you know what if feels like...

I hope you take this all in good humor, this is all true, but very tounge-in-cheek

---

### Post by quietglow on 2005-12-08
[QUOTE=factotum218]You could have summed up your entire post with that one sentance minus the Edubuntu gloating. [/QUOTE]

Naw, I don't think so. Well maybe, but I WAS trying to avoid doing some work at that point so it wouldn't have been quite the same on my end. :-)

And I would be one sad human being if I were gloating over helping out at a school--I was trying to make a point. I think sometimes people get confused, and begin to forget that there is no room for complaining, really. 

You ask for help, you can point out problems and/or you can fix em'.

---

### Post by quietglow on 2005-12-08
And a note to the original poster:

You might want to check out the page in something other than IE: it looks like it breaks the page (and creates lots of the problems you seem to be having). Works fine in Firefox.

---

### Post by Myst3K on 2005-12-08
I got it working first shot with the same card, and Breezy, using this tutorial

[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

It goes a little more in-depth, as well as setting up the remote...

---

### Post by quietglow on 2005-12-08
Man I never saw that page--great link! I can't wait to get home to see if I can finally get my remote working!

---

### Post by JimS on 2005-12-08
I Think I saw an article on Myth TV in
the December issue of Linux Pro Mag.

JimS

---

### Post by Micro Rotors on 2005-12-08
quietglow,

I am sorry if it sounded like I was putting you down for your time  and hard work you have done with the How-To-Guide, it was not my intension at all and I believe I stated that from the get go. 

**I DID** use Firefox to view the guide with as it was all done on Ubuntu. 

I hope the next thing I say will not further tick you off or others here so I am putting on my flame suit now.

If you are putting a how to up on a bulletin board, its purpose is to help others do something that they do not know how to do themselves and being that, it should be gone over with a fine toothed comb to make sure to the best of the authors knowledge that everything has been done to make sure it is correct for the average joe / or less, to be able to understand it. Maybe it was posted before that I don't know, but there were a lot of flaws, in fact to many to be completed as you say you have done with exactly what you posted, IMHO! 

Again, **I DO** believe what you did had GREAT intension's and I thank you for what you have done, I know its not easy to do write ups as I have done them in the past with other than computing topics. I have learned from what I have tried to correct so I guess there is the silver lining in all this.

---

### Post by quietglow on 2005-12-08
[QUOTE=Micro Rotors]

I hope the next thing I say will not further tick you off or others here so I am putting on my flame suit now.

[/QUOTE]

Nothing here is close to ticking me off--man I have people in my office every day demanding that I fix x,y and z on their computer and they ARE the people whos stuff I HAVE to get workin'.

I used an existing HOWTO, and managed to get some differnt hardware working pretty darn easily. I was happy about that so I tried to document what I did differently. I made mistakes--my goal was not making a HOWTO at that point, but getting my sweet PVR set up. I did that. I've had to do it a couple more times since because of trying to get various things working on my box. I've tried to make it better each time. I wish I could have made it perfect from the start. But given that I've had several people email me after having gotten things working, I'd say it was better to have posted it less than perfect and use the effort of the group to get things shaped up. Do we wait until Ubuntu is itself perfect (or anywhere near!) before using it?

Where you come in, is if you post a specific problem, and we fix it, then I can add/note/whatever in the Howto. So it gets better. Things like CDs not having the driver needed etc. are things that I could never discover or fix on my own. Now I know I need to post the driver as part of the process.

Given the fact that I like a challange, there is nothing I'd like better that to get you set up. So lets do it!

---

### Post by Micro Rotors on 2005-12-09
[QUOTE=quietglow]
Given the fact that I like a challange, there is nothing I'd like better that to get you set up. So lets do it![/QUOTE]

oky,doky, well I have reinstalled a new breezy and am going through the install now, I am wondering if I have been having trouble because of this line.

[PHP]sudo apt-get install linux-headers-386[/PHP]

I am running breezy x86 on a amd64 3500+ prossesor

Is this the line I need to run, or would that change because of what you have in your How-To..... 

> OK, let&#8217;s add some kernel headers. Unless you are running a different kernel than stock this should be sufficient. If you are, say running, a K7, AMD64, etc... kernel substitute where appropriate.

Quietglow..... Thanks for your help!!!!! ;)

---

### Post by quietglow on 2005-12-09
[QUOTE=Micro Rotors]
Quietglow..... Thanks for your help!!!!! ;)[/QUOTE]

No sweat g. 

The kernel headers you need to install are gonna depend on whether you're running a 64 bit system. Did you use the 386 version of Breezy or the 64 bit? Pick the kernel headers appropriately.

The easiest way to get your headers is to just open Synaptic (System>admin>synaptic) and then do a search for 'linux headers' and then find the one which matches your kernel. Click and apply.

---


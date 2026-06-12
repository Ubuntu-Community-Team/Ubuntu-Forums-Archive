---
title: "Still working on Wine"
date: 2006-07-20
forum: Desktop Environments
---

### Post by Orion2014 on 2006-07-20
Ok, so heres the skinny, 

i posted about a week or so back but i couldnt find my thread, anyway, im trying to get a program to run under linux, and its one many people dont have experience with, anyway. I got it to install,  i went and set the .exe to open under wine, and it installed no problem. (im using the latest wine, i always keep dapper updated)

well, when i go to run it, it gave me a list of .dlls i needed, so i copied them into the system32 folder in .wine, and then it showed the programs splash screen and gave me this,

[[IMG]http://img242.imageshack.us/img242/259/screenshothy6.png[/IMG]](http://imageshack.us)

Can anyone decipher this, or if anyone recognizes the program and knows what it is and you have it running could you tell me how to do it. Thanks for the help. (and no negativity plz, those who know the program know what i mean)

---

### Post by mattisking on 2006-07-20
It looks like you've encountered incomplete parts of wine. Try updating your repositories:

[http://winehq.org/site/download-deb]("http://winehq.org/site/download-deb")

---

### Post by Orion2014 on 2006-07-20
ok, now i can do that from synaptic, correct?

im sorry, im fairly new, can you explain how to do that please.:confused:

---

### Post by Orion2014 on 2006-07-20
Ok, UPDATE!!!

I completely removed wine and reinstalled it, still the same screen as the one showed above.

Im TOTALLY stumped, someone plz help!

Could it be that the latest version (0.9.17) could just be faulty?

---

### Post by n00buntu NJ on 2006-07-20
Hello, 

I almost didn't read your thread because I really only use wine for one program, so I didn't think I could help.  Lucky for you that one program is WTLIB 2005!

After many ADHD attempts at installing this program under Wine, I finally slowed down for a second and followed [these]("http://appdb.winehq.org/appview.php?iVersionId=4154") instructions and got it to work within minutes.

I'll c&p too, just to make it easier.  I don't take any credit for this, so thank google.  :cool:  


[I]
1. start from scrach (remove ~/.wine directory)
2. run winecfg. Chose "Windwows XP" as windows version.
3. copy comctl32.dll from a windows XP (license is needed for this :-(

cp comctl32.dll ~/.wine/drive_c/windows/system32/

3. mount cdrom if you haven't and run the setup program as:

WINEDLLOVERRIDES=comctl32=n wine /media/cdrom/Setup.exe

4. Run the install as normal. Be aware that the copy progress bar wil not be displayed. Let it work for 2-5 minutes and an "InstallShield Wizerd Complete" dialog will appear.

5. start wtlib from the MEPSCommon:

cd ~/.wine/drive_c/Program Files/Watchtower/MEPSCommon/
wine ../Watchtower Library 2005/e/wtlib.exe

replace the "/e/" with your language (I use "/n/" for Norwegian here)

You could create a script starting wtlib from the proper location.

Tested with Norwegian wtlib 2005.

Note that you will only need the comctl32.dll to run the install program. Here wine craches if the native comctl32 is used to run wtlib after its installed.

A few things that does not work properly:

* Some of the default sizes of the fields are wierd. For example, it looks like you cannot select a scripture in the Bible, but its just to grab the horizontal bar with the mouse and resize. Its important to find all those and do this if you are helping a real newbie.

* Change the date for the daily text. You can change the date but the display does not update.

* hovering scriptures does not show the scripture in tooltip.

Otherwise it works pretty well.

Now, please go back to your personal study ;)
[/I]

If you need some help you can email me - just click on my username above this post and shoot me an email.

---

### Post by mattisking on 2006-07-21
> **Orion2014 said:**
> ok, now i can do that from synaptic, correct? im sorry, im fairly new, can you explain how to do that please.:confused:

Sorry about that... I was at work and away from my Linux machine so I had to be a little more vague. Also, the link to winehq seemed to be down at that moment.

1. From a terminal window, type this:
sudo gedit /etc/apt/sources.list

2. Scroll down to the bottom of that file and add the one relevant to you depending on whether you are running Dapper (the latest release) or Breezy (the previous one):
For Ubuntu Dapper (6.06):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
For Ubuntu Breezy (5.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) breezy main

3. Save and exit gedit (the text editor).

4. from that same terminal:
sudo apt-get update
sudo apt-get dist-upgrade

It will ask for passwords and such. Because you already have wine installed, you should just have to accept whatever upgrades are offered. Unfortunately, this doesn't necessarily mean it will be fixed, but this version of wine is much newer and more up to date than what was released in Dapper.

---

### Post by Orion2014 on 2006-07-21
Yeah, I did all that. Im going to do what n00buntu laid out for me, it seems he knows exactly how to do what im trying to do. Im just going to have to go by it step by step, seems thats my best chance.

Thanks for all the help guys.

---

### Post by n00buntu NJ on 2006-07-22
> **Orion2014 said:**
> Yeah, I did all that. Im going to do what n00buntu laid out for me, it seems he knows exactly how to do what im trying to do. Im just going to have to go by it step by step, seems thats my best chance.

Thanks for all the help guys.


Let me know how it goes...  I know it will work because I've done it twice.

:cool:

---

### Post by Orion2014 on 2006-07-25
I guess I should post the fact that I got it working, and it was alot simpler than i thought. Runs great in wine, I love Ubuntu Linux.

---


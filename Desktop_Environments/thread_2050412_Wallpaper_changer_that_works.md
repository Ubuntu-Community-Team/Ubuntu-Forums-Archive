---
title: "Wallpaper changer that works"
date: 2012-08-30
forum: Desktop Environments
---

### Post by rmcellig on 2012-08-30
I just installed Xubuntu 12.04 on my laptop and am looking for a wallpaper changer that works. I tried the ones in the Software center and none of them work at all. Am I doing something wrong? I tried Variety, Wally, Wallch, Slidewall. None of them work at all. I'm sure I am doing something wrong. Please asdise how I can get one of the screensavers to work. Thanks!!

---

### Post by Toz on 2012-08-30
With respect to a wallpaper changer, try this:

1. In SettingsManager -> Desktop, select the "Image List" option and add to the image list, the wallpapers that you want to cycle.

2. Create a cron entry to reload xfdesktop (which in turn will change the wallpaper to a random one in the list you created in step #1. To do so, in a terminal window, enter the following command:
```
crontab -e
```
...and use your arrow keys to go to the bottom of the file and add the following line:
```
*/15 * * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1
```
...note, the /15 refers to the change frequency time - in the example above, it will cycle every 15 minutes. To make it cycle for example every 5 minutes, us "/5" instead.

Then, to save the file:
- ctrl+x
- Y
- <press the enter key>

> Please asdise how I can get one of the screensavers to work. Not sure what you mean here.

---

### Post by rmcellig on 2012-08-31
Thanks. I will try that and see what happens.

Regarding my last statement:


Quote:
Please advise how I can get one of the screensavers to work.


What I meant to say was
Quote:
Please advise how I can get one of the desktop wallpaper changers to work.

---

### Post by rmcellig on 2012-08-31
Like this?

---

### Post by LewisTM on 2012-08-31
Maybe I'm missing something but doesn't the Xfce Desktop Settings dialog offer the option to shuffle the image list every X minutes??

Works perfectly here.

EDIT: Oops, that only applies to Xfce 4.10. Well there's another valid option for you :)

---

### Post by rmcellig on 2012-08-31
I thought it did as well. Maybe that's only in the 4.10 version? 12.04 uses 4.8.

---

### Post by LewisTM on 2012-08-31
Why not install 4.10 from the PPA? It's perfectly safe and brings in new features.
[https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)

Enjoy!

---

### Post by rmcellig on 2012-08-31
Thanks. I will do that. I just wanted to make sure it was safe to do this.

---

### Post by rmcellig on 2012-08-31
Once I install the ppa do I just do a sudo apt-get update/upgrade?

---

### Post by LewisTM on 2012-08-31
> **rmcellig said:**
> Once I install the ppa do I just do a sudo apt-get update/upgrade?
```
sudo apt-get update && sudo apt-get install xubuntu-desktop -y
```

---

### Post by hakermania on 2012-08-31
I am one of the developers of Wallch and I want to let you know that the newest versions of Wallch work perfectly under XFCE (I tested it  personally). These are beta versions of Wallch (stable, though), just before the 4.0 version of Wallch :)

To install the latest version you can download the deb from here:
[https://launchpad.net/~wallch/+archive/3+/+packages](https://launchpad.net/~wallch/+archive/3+/+packages)

Or you can install the ppa and get automatic updates:

```
sudo add-apt-repository ppa:wallch/3+
sudo apt-get update && sudo apt-get install wallch
```

Just head to the _Edit->Set Custom Command_ dialog and there you can set your desktop environment or set a command of your own (completely yours)!!!

---

### Post by rmcellig on 2012-08-31
Thanks so much!! I will give it a try. There is nothing special I have to do after installing it?

---

### Post by hakermania on 2012-08-31
> **rmcellig said:**
> Thanks so much!! I will give it a try. There is nothing special I have to do after installing it?

Read the last thing I mentioned in my reply for this.

Please be careful NOT to install any recommended packages you may not need for Wallch! Generally, do not install anything that it may require the installation of Nautilus or something like that.... But, we were careful to have these packages as recommended only :)

---

### Post by nothingspecial on 2012-08-31
> **rmcellig said:**
>  There is nothing special I have to do after installing it?

Nope, I've got nothing to do with it :p

---

### Post by hakermania on 2012-08-31
> **nothingspecial said:**
> Nope, I've got nothing to do with it :p


[idiot]Good it worked for you ?[/idiot]


Nevermind, I'm an idiot. :D

---

### Post by vasa1 on 2012-08-31
> **rmcellig said:**
> Thanks so much!! I will give it a try. There is **nothing special** I have to do after installing it?

You have to choose your words carefully ;)

---

### Post by rmcellig on 2012-08-31
What would I have to do to get this code to work in Lubuntu 12.04 or ubuntu 12.04?

*/15 * * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1

---

### Post by hakermania on 2012-08-31
> **rmcellig said:**
> What would I have to do to get this code to work in Lubuntu 12.04 or ubuntu 12.04?

*/15 * * * * DISPLAY=:0.0 xfdesktop --reload > /dev/null 2>&1

Wait. I'm not sure who are referring to now. Have you tried Wallch?

---

### Post by rmcellig on 2012-08-31
Toz posted code at the beginning of this thread for me to try out. It works great. AS I am still learning Linux, I wanted to know if I could modify this code so it would work in Lubuntu as well as Ubuntu.

As far as Wallch, I installed it on both my laptops and set the settings to XFCE as you suggested and then pressing the Apply button. Sometimes it worked and sometimes nothing. I had to go back into Wallch and hit the start button again. Not sure why this happened.

---

### Post by hakermania on 2012-08-31
> **rmcellig said:**
> Toz posted code at the beginning of this thread for me to try out. It works great. AS I am still learning Linux, I wanted to know if I could modify this code so it would work in Lubuntu as well as Ubuntu.

As far as Wallch, I installed it on both my laptops and set the settings to XFCE as you suggested and then pressing the Apply button. Sometimes it worked and sometimes nothing. I had to go back into Wallch and hit the start button again. Not sure why this happened.

If you read the Docs, it says that pressing the Apply button will make Wallch use this command from now on. Then, pressing the start button will make the Wallch change the wallpapers with this buttons. I don't understand where you stuck.

---

### Post by rmcellig on 2012-08-31
Ya it's strange because I did what you mentioned in your last post. When I am in Wallch, do I have to select all the wallpaper in the list before pressing the start button? I'm in the middle of installing Lubuntu on my computer but what I will do is post back the steps I took to invoke the wallpapers changing. Stay tuned.... :)

---

### Post by hakermania on 2012-08-31
No, you don't have to select all of them. Wallch will start changing the wallpapers from the current list at the time you tell it. I don't think it could be simpler...

---

### Post by xfctr on 2012-09-02
Hello. Author of Variety here. Recent releases of Variety work well on Xubuntu 12.04, Lubuntu 12.04 and latest Linux Mint (all tested by me), the one in the software center is just way too old and the support team there is too slow to update it.

To install the latest version:
```
sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update
sudo apt-get install variety
```

More info about Variety here: [https://launchpad.net/variety](https://launchpad.net/variety)

---

### Post by hakermania on 2012-09-02
> **xfctr said:**
> Hello. Author of Variety here. Recent releases of Variety work well on Xubuntu 12.04, Lubuntu 12.04 and latest Linux Mint (all tested by me), the one in the software center is just way too old and the support team there is too slow to update it.

To install the latest version:
```
sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update
sudo apt-get install variety
```

More info about Variety here: [https://launchpad.net/variety](https://launchpad.net/variety)

Wallpaper Changer Fight!!!

---

### Post by rmcellig on 2012-09-02
Finally I got Wallch working on all three of my computers. I had to tweak some of the settings. 

Now it looks like I have an alternative (Variety) to try out.Thanks for posting the PPA. Competition is good. I'll have to see how easy Variety is to get going compared to Wallch. Stay tuned!

---

### Post by hakermania on 2012-09-03
> **rmcellig said:**
> Finally I got Wallch working on all three of my computers. I had to tweak some of the settings. 

Now it looks like I have an alternative (Variety) to try out.Thanks for posting the PPA. Competition is good. I'll have to see how easy Variety is to get going compared to Wallch. Stay tuned!

Would you mind telling me which settings you had to tweak (because it worked out of the box from me, from just changing the setting from the custom command dialog)?

Thanks :)

---

### Post by rmcellig on 2012-09-03
These are the settings that worked for me.

---

### Post by gattofix on 2012-09-23
Hi,

I discovered this thread by chance and after I tried Wallch, I could finally change the default wallpaper. 

I am using Xubuntu 12.04 and I could actually change the wallpaper using the desktop settings dialogue, but after logging out or restarting, it was back to the default wallpaper and I had to change it to my wallpaper once again. I found out that someone already signaled this as a Xubuntu bug.

Anyway, Wallch looks great overall.

Some observations: I am not quite sure about the "custom command". Is it necessary for XFCE? If I choose it for XFCE from the menu, the next time I go back there "Gnome 3" is activated again. So do I only have to use the XFCE command once? For me as a newbie this is not clear enough, also I would not know about changing the command sequence.

Then, I wanted to just use Wallch to change the wallpaper (once). There is exactly that option in the "startup" menu. However, acccording to the help infos, it just picks one wallpaper from the specified list randomly. What if I want Wallch to just change the background to one specific wallpaper and keep it that way? I tried to achieve that by just leaving one wallpaper in the list, but then Wallch complains. It would be great if you could implement such an option, especially in the light of the Xubuntu 12.04 wallpaper bug.

Lastly, changing the "style" of wallpapers never changes anything. It always zooms, no matter what the setting is. I have a monitor with a resolution of 1600x1200.  So in case I have a widescreen wallpaper and set Wallch to "center", it should show the complete wallpaper and leave a black frame at the top and bottom, right? Admittedly, usually this is not how I would use it, but, with this Live Earth option activated, I can never see the whole world map if it zooms, and here I would much prefer to put up with the black frame. It would be great if this worked, and if Wallch would also immediately show any changes in style (preview).

I have one more idea for a future version. Let's say I have downloaded ten new wallpapers, some in 4:3, some in 16:9 format.  With my 4:3 monitor, it would be fantastic if I could specify individually for each wallpaper in which style I would like to watch it. It would be even greater if you could, after specifying your monitor aspect ratio, select via a movable frame which section of the wallpaper should be selected for display. You know, sometimes I would cut off the right-hand part, sometimes the left-hand part, sometimes I would choose the middle for display. I realize that implementing this would take some effort, but such a function would be much easier for the user than changing all the wallpapers with an image editor to his taste.

I am looking forward to some feedback.
gattofix

---

### Post by hakermania on 2012-09-23
> **gattofix said:**
> Some observations: I am not quite sure about the "custom command". Is it necessary for XFCE? If I choose it for XFCE from the menu, the next time I go back there "Gnome 3" is activated again. So do I only have to use the XFCE command once? For me as a newbie this is not clear enough, also I would not know about changing the command sequence.


Yes, the custom command should be necessary to everything different from GNOME 3. The custom dialog switches back to GNOME 3 because it does not remember what you've chosen the last time, but in fact, you are still using the XFCE command. We knew that this is wrong so we've already fixed it (available at the next version)

> **gattofix said:**
> 
Then, I wanted to just use Wallch to change the wallpaper (once). 

Just double click on your preferable wallpaper from the list.
> **gattofix said:**
> 
Lastly, changing the "style" of wallpapers never changes anything.

This works only under GNOME 3 ! Workspaces have different options for the image's style. Some of them don't have any.



I have no time right now but I will read in detail your feature request and I will let you know :)

---

### Post by gattofix on 2012-09-23
@hakermania

Thanks for the fast reply!

You say I can change the wallpaper (once) by double-clicking on a wallpaper in the list. Well, I knew you could do that, but of course I want the custom wallpaper to be sticky. I can change the default wallpaper in XFCE via the desktop settings, as well, but, as I pointed out, after reboot the default wallpaper (blue lake / trees) is back.

Can I use Wallch to simply change to my favourite wallpaper and have Xubuntu keep it that way? I mean, this should be the most basic function, shouldn't it?

Thanks for clarifying that the "styles" only work in Gnome 3. I wouldn't have expected that. I guess then my request for an individual option of which style to apply to which particular wallpaper is - at least for XFCE - pointless or at least a bit hard to implement.

---

### Post by Open Source Noob on 2012-09-23
I downloaded a wallpaper changer app called "Variety" during the Ubuntu App Showdown, it work's really well and has quite a few fancy options besides just changing the wallpaper every x number of minutes
 
[https://launchpad.net/variety]("https://launchpad.net/variety")

Easy install
```
sudo add-apt-repository ppa:peterlevi/ppa
sudo apt-get update
sudo apt-get install variety
```

---

### Post by hakermania on 2012-09-24
> **gattofix said:**
> 
Can I use Wallch to simply change to my favourite wallpaper and have Xubuntu keep it that way? I mean, this should be the most basic function, shouldn't it?

The most basic function for Wallch is to set your desktop wallpaper based on a list and NOT to overcome XUbuntu bugs. If XUbuntu has the bug of resetting to the default wallpaper, then Wallch has nothing to do with it.

In other words, if a company bring a table to your house and your child broke it each time and you had to buy a new table every time, it isn't the company's fault :)

> **gattofix said:**
> 
Thanks for clarifying that the "styles" only work in Gnome 3. I wouldn't have expected that. I guess then my request for an individual option of which style to apply to which particular wallpaper is - at least for XFCE - pointless or at least a bit hard to implement.
Not so hard to implement, but think that every Desktop Environment has its own style preferences and we have to search for the corresponding commands etc for each of them individually. Also, there have to be made extra checks for every start of Wallch so as to see which options should be available under the styling (because, as I said, there are many differences, and some don't even have such option as styling).

So, we stuck with the preferences that are available in GNOME 3, from where most of our users come from.

---

### Post by zeroblitzt on 2012-11-09
I want to throw my hat into the ring here. Just got Variety... very nice application. Plenty of configuration options and a lot of online content to choose from if you don't have your own backgrounds.

Bravo!:KS

---

### Post by ferd on 2012-11-10
Thank you so much for Variety. I feel that I have tried them all until finally finding the one that works: Variety.

---


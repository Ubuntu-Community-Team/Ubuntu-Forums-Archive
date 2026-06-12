---
title: "Anyone using KDE 4.6?"
date: 2011-03-07
forum: Desktop Environments
---

### Post by jeremyjjbrown on 2011-03-07
The last time I tried KDE was 4.2 and I stopped because I felt it lacked features in the context click (right click) menu. I spent a few hours googling to see if I could add the features I needed. There was a lot to like, but that was a deal killer for me. I'm hopeful that four versions later they have added more functionality to the context menu. Do you know?

---

### Post by wizard10000 on 2011-03-07
I'm running 4.6.1 - but your question is kinda vague.  What functions are you looking for in the context menu?

---

### Post by inobe on 2011-03-07
> Anyone using KDE 4.6?

yo :D

looks good, nothing out of place.

if you'd like, i can take several snapshots for you?

---

### Post by TBABill on 2011-03-07
I'm using it on PCLinuxOS and it's sweet. Very fast desktop and functions well, plus the Lancelot menu is much more appealing to the eye.

---

### Post by ankspo71 on 2011-03-07
Hi,
If you decide to upgrade Kubuntu (or KDE) you can install various Service Menus to give you more options in the right click menu. You can search for  "service menu" in your package manager, or find some at kde-look.org in the service menus category of the site.

After you have installed a new service menu, you can enable and disable them by opening Dolphin, then go to the Settings menu > Configure Dolphin > Services. There is also a button there to download new service menus from kde-look.org.

I think some of the older service menus are not compatible with dolphin and use konqueror instead.
Hope this helps.

PS: I'm using KDE 4.6.1 and it's doing great, but I get an occasional crash while changing theme preferences in System Settings.

---

### Post by jeremyjjbrown on 2011-03-07
>  Service Menus to give you more options in the right click menu.

Great! Sometimes just knowing what to call the package is 90% of the work. Thanks!

---

### Post by PaulW2U on 2011-03-07
> **ankspo71 said:**
> PS: I'm using KDE 4.6.1 and it's doing great, but I get an occasional crash while changing theme preferences in System Settings.
I get that too using Kubuntu 11.04 alpha 3. I'm currently checking to see if a bug report has already been submitted, it probably has but it's very time consuming wading through all the bug reports.

Otherwise KDE 4.6.1 is a great improvement over everything that I've tried from KDE in the past and if a couple of bugs can be fixed I'll be staying with this version.

---

### Post by BigSilly on 2011-03-07
I'm using KDE4.6.1 on PCLinuxOS too. Absolutely gorgeous. I love it to bits. I'm getting a minor bug occasionally when changing wallpaper, where the screen goes completely black, but it's easily sorted.

KDE4 has rocketed forward imho, and PCLOS is a joy with it too.

---

### Post by oldos2er on 2011-03-07
I'm using KDE 4.6 and enjoying it very much.

---

### Post by inobe on 2011-03-10
the only thing that bugs me is the missing mass of kde extras, i have to build it, i guess we can blame a 700mb cd for that.

knowing exactly what these extras are helps considerably.

someone should compose a HowTo article on this :D

as much as i know about the extras, im certain that there are ones i missed :P

---

### Post by malspa on 2011-03-10
Another one using 4.6.1 in PCLOS. Looks great so far.

---

### Post by Taltos DCLXVI on 2011-03-10
I'm using kde, i looks great, i'ts functional and beautiful.

---

### Post by Ichtyandr on 2011-03-13
I installed kde 4.6.1 on Maverick from kubuntu backports ppa on my main desktop
I would have switched to natty already, but my binary nvidia drivers are still missing there and also there are going to be lots of updates and possible breakages, it is alpha after all
On 10.10 it is very stable, beautiful and flexible. Actually I have a feeling that unity desktop will have to do a lot of work to match this polish.

---

### Post by jcolyn on 2011-03-13
I'm using 4.6.1 on Linux Mint 10 and with the exception of the Dolphin issue where the /home folder showed blank it has worked fine for me.

I did fix the Dolphin issue though by going to settings-configure Dolphin and in the location box I eliminated my username which left ```
file:///home/
```

---

### Post by ratcat on 2011-03-17
KDE 4.6.1 ok here, and found an interesting fonts cure. Open Office font display problems on toolbar. With Ubuntu fonts and Ubuntu Mono the fonts are perfect. A big deal here, with such advanced software there's no excuse for bad font display. 
Thanks KDE and Ubuntu

---

### Post by Drone4four on 2011-03-17
How do I find out what version of KDE i have installed by using the command line without actually loading KDE and clicking 'about kde' in the options menu.  I tried the commands kde --version and kde4 --version, but that didn't work.

---

### Post by SeijiSensei on 2011-03-17
```
dpkg -s kdebase-workspace-bin | grep Version
```

On my 4.6.1 system, that returns "Version: 4:4.6.1-0ubuntu1-maverick1-ppa1".  The 4.6.1 after the colon is the version number.

If you drop the "| grep Version" part of the command, you'll see an extensive description of the package and its dependencies.  This works for any package, not just KDE4.

---

### Post by Drone4four on 2011-03-17
Thanks SeijiSensei.  Here is  the version of KDE installed on my system:

$ dpkg -s kdebase-workspace-bin | grep Version
Version: 4:4.5.1-0ubuntu8

---

### Post by liferules on 2011-03-17
I have tried KDE many times over the years as far back as version 2.x. I hated 4.2 but decided to try it again with 4.6 and have to say I love it... The memory used is finally about the same as Gnome (+ or -) and I am probably starting with it. Do I love everything? NO. There are a few programs that I just like better on Gnome (i.e. Gedit, GFTP, and GIMP to name a few). Overall a great job...

---

### Post by OldGaf on 2011-03-22
> **jcolyn said:**
> I'm using 4.6.1 on Linux Mint 10 and with the exception of the Dolphin issue where the /home folder showed blank it has worked fine for me.

I did fix the Dolphin issue though by going to settings-configure Dolphin and in the location box I eliminated my username which left ```
file:///home/
```

Nice one.... this was really bugging me as well in Kubuntu 10.10!

---

### Post by SeijiSensei on 2011-03-22
The Home folder should represent your home directory, not the entire /home tree.  Why is that surprising or annoying?  On systems with more restrictive user permissions than Ubuntu, you wouldn't be able to even list the contents of any other directories under /home anyway.

(Ubuntu assigns 0755 permissions to user home directories; other distributions like RedHat use 0700.  I definitely prefer the latter for obvious privacy and security reasons.)

---

### Post by Alejandro Nova on 2011-03-22
Some caveats.

1. I'm running with Natty now, and I must say: it's more stable than Maverick, right now. Believe me: you'll have the "alpha" sensation of slowness only if you run Ubuntu Natty with Unity, or with GNOME 3. With KDE you'll feel better than with Maverick.

2. Natty benefits from some upgrades that are sorely needed. I think about Akonadi 1.5.1. I reported the upgrade request to Akonadi 1.5.1, I'm running Strigi-trunk with KDE-PIM/Akonadi trunk (both compiled from their Git trees) and everything-semantic-desktop-related-I-could-find-in-Git, and the performance is more than acceptable. For a 3 year old computer, that's good. The thing boots in two minutes... but that includes setting up the Akonadi Event List plasmoid and the Lionmail plasmoid, two things you'll never see because they are experimental or are in obscure source repositories. Also, the event list is usually full because it's synced with Facebook.

3. KDE 4.6.1 is the **first KDE release in which you can use the Nepomuk Semantic Desktop as intended**. Enable all Nepomuk related options, including the Nepomuk file search in KRunner and the Contact search, even if they didn't work before for you. You'll be amazed at the speed and low resource consumption (remember, you REQUIRE KDE 4.6.1 TO SEE THIS, 4.6.0 IS BUGGY STILL).

4. The lower/higher memory consumption compared to GNOME is a myth: KDE spends a bit more memory, but for a lot more functionality. Add Beagle, GDesklets and AWM to the GNOME memory consumption, and you can begin to make fair comparisons.

5. Ditch Amarok. Bangarang 2 can do 80% of what Amarok does, with 20% of the memory eaten by Amarok. A good application of the 80/20 rule. If you require library-based features, Clementine. 

6. If you want screenies, you'll have screenies.

---

### Post by Admiral5264 on 2011-03-22
I am currently using KDE 4.6, although i wish i could figure out how to install themes on it -.- I see it is different  than previous KDE versions in that regard. So if any of you would be kind enough to help me out on this I'd be appreciative.

---

### Post by ivanovnegro on 2011-03-31
> **Admiral5264 said:**
> I am currently using KDE 4.6, although i wish i could figure out how to install themes on it -.- I see it is different  than previous KDE versions in that regard. So if any of you would be kind enough to help me out on this I'd be appreciative.

What do you mean exactly with themes, as to install them is really easy.
You can install new icons, themes etc. form the KDE system settings.
Be more precise and I will say you step by step what you have to do.

Btw, Im using now KDE 4.6.1 and it is as fast as is my Gnome desktop.

---

### Post by malspa on 2011-04-02
Just got KDE 4.6.1 in Fedora 14 last night. Looks good so far.

---

### Post by cookiecruncher on 2011-04-03
> **Alejandro Nova said:**
> Some caveats.

3. KDE 4.6.1 is the **first KDE release in which you can use the Nepomuk Semantic Desktop as intended**. Enable all Nepomuk related options, including the Nepomuk file search in KRunner and the Contact search, even if they didn't work before for you. You'll be amazed at the speed and low resource consumption (remember, you REQUIRE KDE 4.6.1 TO SEE THIS, 4.6.0 IS BUGGY STILL).



Nepomuk crashes each time I boot up into 4.6.1.  I disabled it.

Otherwise it's looking good.

---

### Post by SeijiSensei on 2011-04-03
I'm happy to report that the annoying [panel auto-hide bug]("https://bugs.kde.org/show_bug.cgi?id=258012") is fixed in 4.6.2, which the Kubuntu devs say will be [released to backports]("http://kubuntuforums.net/forums/index.php?topic=3116181.0") later this week.

---

### Post by jcolyn on 2011-04-03
> **SeijiSensei said:**
> I'm happy to report that the annoying [panel auto-hide bug]("https://bugs.kde.org/show_bug.cgi?id=258012") is fixed in 4.6.2, which the Kubuntu devs say will be [released to backports]("http://kubuntuforums.net/forums/index.php?topic=3116181.0") later this week.

So far my only issue with this has been when I open Gimp the layers, channels, path, etc bar in the task manager flashes till I click it with the mouse. The panel then auto-hides like it should.

Hopefully 4.6.2 will fix it..

---

### Post by jeremyjjbrown on 2011-04-10
This thread turned out to yield more insight than I had hoped. Somehow my locale settings in my Ubuntu refuse to allow themselves to be rebuilt. I will probably rebuild my laptop and may just give Kubuntu a spin again.

Thanks!

---

### Post by SeijiSensei on 2011-04-10
Try running this from a command prompt:

```
sudo dpkg-reconfigure locales
```

System Settings doesn't always do a very good job about prompting for root permissions when they're needed.  I tried to change my NTP server today using the Date/Time applet and was entirely frustrated because the applet doesn't invoke kdesudo.  I could easily change my server by editing /etc/ntp.conf manually as root and restarting ntpd.  In KDE I had my ordinary user privileges and thus cannot edit a root-owned file like that.  I can imagine the same problems might arise trying to change locales from within KDE as well. 

I gave up trying to configure printers with KDE for this very same reason.  I now use a browser and talk to CUPS directly at [http://localhost:631/](http://localhost:631/).

By the way, you should all have been updated to 4.6.2 a couple days back.

---

### Post by jeremyjjbrown on 2011-04-10
> sudo dpkg-reconfigure locales

Thanks but I've tried that on already. The root of my issue is a mismatch between the Locale setting and my libc versions as well as missing values I can't get to generate. I'd really, really like to know how it happened, but I've wasted several hours on it already and could have nuked and paved in less than an hour.

---

### Post by jeremyjjbrown on 2011-04-11
so I now have Kububtu 10.04 installed on one of my laptops.

My first impression is a reminder that Windows 7 look and feel is a total rip off of KDE. KDE is lovely and I'm glad I won't have to waste time moving menu bar buttons back were they belong, making a side menubar functional or purging Mark Shuttleworths garish color tastes from my machine.

On to my first quibble. Can anyone tell me how to have only one icon per application on the panel? I keep a lot of windows open and three different chrome icons, two terminals and a text editor is just not going to work out if they each must have their own icon.

---

### Post by ivanovnegro on 2011-04-11
> **jeremyjjbrown said:**
> so I now have Kububtu 10.04 installed on one of my laptops.

My first impression is a reminder that Windows 7 look and feel is a total rip off of KDE. KDE is lovely and I'm glad I won't have to waste time moving menu bar buttons back were they belong, making a side menubar functional or purging Mark Shuttleworths garish color tastes from my machine.

On to my first quibble. Can anyone tell me how to have only one icon per application on the panel? I keep a lot of windows open and three different chrome icons, two terminals and a text editor is just not going to work out if they each must have their own icon.

For the icons, right click on the panel, choose smooth tasks, in the first entry you have to group the tasks, then you go to the second one, I think Layout, expand tasks, and there set expand to none. Im not a native English speaker btw and I use KDE 4.6.2, so that could be different on Kubuntu 10.04.

---

### Post by ankspo71 on 2011-04-11
> **jeremyjjbrown said:**
> 
On to my first quibble. Can anyone tell me how to have only one icon per application on the panel? I keep a lot of windows open and three different chrome icons, two terminals and a text editor is just not going to work out if they each must have their own icon.

Hi,
I like using "plasma-widget-smooth-tasks" to handle this type of job.:) It is in Ubuntu's repositories so you can install it using your package manager (Kpackagekit, Synaptic, etc). You add it to the panel by right clicking on the panel (and unlock widgets if necessary) > panel options > add widgets, then select 'smooth tasks'. It's very configurable too. Here's a screenshot of smooth tasks:

---

### Post by antyloois on 2011-04-11
the only thing that bugs me is the missing mass of kde extras, i have to build it, i guess we can blame a 700mb cd for that. 2945abc45 0411

knowing exactly what these extras are helps considerably.

---

### Post by jeremyjjbrown on 2011-04-11
So far so good with KDE! I especially love the Klipper tool built right in. I like the side tabs in Kate, as well as the increased functionality over Gedit. To bad I started using Linux around KDE 4.1, I think I should have switched much earlier. 

Thanks for smooth tasks ankspo71 and ivanovnegro. It's very minor, but is there anyway to 'pin' an icon into the smooth tasks area so it also acts as a launcher?

---

### Post by ivanovnegro on 2011-04-11
> **jeremyjjbrown said:**
> So far so good with KDE! I especially love the Klipper tool built right in. I like the side tabs in Kate, as well as the increased functionality over Gedit. To bad I started using Linux around KDE 4.1, I think I should have switched much earlier. 

Thanks for smooth tasks ankspo71 and ivanovnegro. It's very minor, but is there anyway to 'pin' an icon into the smooth tasks area so it also acts as a launcher?

If I understand you right, yes. Go to your applications in the Kick Off and add them with a right click to the panel as a launcher. Maybe you have to switch before it to the old K-Menu, then its definiteley possible and then switch back to Kick Off.

---

### Post by ankspo71 on 2011-04-11
> **jeremyjjbrown said:**
> It's very minor, but is there anyway to 'pin' an icon into the smooth tasks area so it also acts as a launcher?

We can't pin any applications into smooth tasks itself, but we can pin any application icons to the panel right next to smooth tasks. BTW, Most docks will work well with KDE4 too. 

This is for anyone new to KDE:
To add application launchers to the panel:
Right click on your panel and unlock the widgets if necessary, then go your start menu and right click on any application and choose "add to panel". 

To move application launchers on the panel:
Right click on your panel and unlock the widgets if necessary, then right click on the panel again and choose panel options >     panel settings. Hover over the widgets in the panel and you will see arrows appear. Drag those arrows left and right to reorder your widgets. When done reordering the widgets,  click on the red close button to close the settings, then lock the widgets again.

---

### Post by jeremyjjbrown on 2011-04-11
> **ankspo71 said:**
> We can't pin any applications into smooth tasks itself, but we can pin any application icons to the panel right next to smooth tasks.

The Dev for Smooth-Tasks is adding the pin function for future versions according to his notes on KDE-look. So I'm looking forward to that. Putting my launchers in favorites will do for now. I have my machine totally set up after three terminal commands, and a few mouse clicks to set up the panel, and disable the (annoying to me) wallet app. Getting Gnome the way I like it took much, much longer. I was worried about what I would have to do with Gnome 3 since I had tried the beta and not liked it at all. If things keep going this smoothly I'm going to switch my wife's notebook over too.

---

### Post by rosencrantz on 2011-04-11
> **liferules said:**
> I have tried KDE many times over the years as far back as version 2.x. I hated 4.2 but decided to try it again with 4.6 and have to say I love it... The memory used is finally about the same as Gnome (+ or -) and I am probably starting with it. Do I love everything? NO. There are a few programs that I just like better on Gnome (i.e. Gedit, GFTP, and GIMP to name a few). Overall a great job...

Gimp is GTK built, but I'd not say it's Gnome specific - AFAIK it doesn't depend on the Gnome libraries and it's included in every major KDE distribution, as a number of other GTK based apps like Firefox, Inkscape or Chrome. Natty apparently comes with an Oxygen GTK theme to smooth things over aesthetically - I can't wait ;-)

---


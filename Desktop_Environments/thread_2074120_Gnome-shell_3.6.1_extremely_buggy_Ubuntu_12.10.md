---
title: "Gnome-shell 3.6.1 extremely buggy Ubuntu 12.10"
date: 2012-10-21
forum: Desktop Environments
---

### Post by Phaze08 on 2012-10-21
I've been a good fan of gnome-shell for a long time. I've been using it since it came around not long ago and I just love the extensions, themes, and speed of it. Ever since I upgraded though, its pretty buggy. 
First, when I enable user themes, and I press super key to show open windows, the shell crashes. 
Second, all my extensions disable every time I log in (I've updated the ones that are available on extensions.gnome.org)
Also, when I get system notifications, those new ones in shell v 3.6.1, it just pops up right in the center of the screen, except instead of the notification, its just the app icon, and when I click, it just goes away and nothing else happens lol. 
Anyone else having these issues?

On a side note, anyone know a good app to replace Ubuntu Tweak since its been discontinued?

---

### Post by stbub on 2012-10-22
> **Phaze08 said:**
> 
Anyone else having these issues?


Well, I'm not that demanding on what I need in gnome shell.

But the right side virtual desktop panel seems to vanish rather quickly.

And what happened to the automounting of usb drive?  Not working anymore.

What's the point in making such buggy ubuntu release? :-(

---

### Post by fisadev on 2012-10-31
> **Phaze08 said:**
> I've been a good fan of gnome-shell for a long time. I've been using it since it came around not long ago and I just love the extensions, themes, and speed of it. Ever since I upgraded though, its pretty buggy. 
First, when I enable user themes, and I press super key to show open windows, the shell crashes. 
Second, all my extensions disable every time I log in (I've updated the ones that are available on extensions.gnome.org)
Also, when I get system notifications, those new ones in shell v 3.6.1, it just pops up right in the center of the screen, except instead of the notification, its just the app icon, and when I click, it just goes away and nothing else happens lol. 
Anyone else having these issues?

On a side note, anyone know a good app to replace Ubuntu Tweak since its been discontinued?

I have the same issues, plus some other issues like some extensions settings not being saved, and nautilus 3.6 settings working really weird :/

---

### Post by grege on 2012-11-03
A lot of problems are caused by themes. A lot of themes that worked fine in 3.4 will cause havoc in 3.6. Start with the stock theme and see what happens.

I am using a theme called XGnome Enhanced and it runs well. I have used supposed 3.6 themes that wrecked the notification area and mounting/unmounting USB had to be done through Nautilus.

Finally, mine is a clean install using UGR and does not have any Unity installed. The extensions on extensions.gnome.org are just catching up, most work but I have had to go to GitHub for some of my favourites.

Early days.

---

### Post by Frogs Hair on 2012-11-03
I would agree with the post above. Any problems I have had with the Gnome shell have been theme related. Use Gnome 3.6 themes only because some of the 3.4 themes even though they appear to display properly don't work correctly. 12.10  has been a great release for me but I also never upgrade. I tried only once.

---

### Post by grahammechanical on 2012-11-04
> What's the point in making such buggy ubuntu release? 

Why do you blame Ubuntu and not Gnome for releasing a buggy Gnome shell?

When I search for Gnome Shell in the Ubuntu Software Centre and click 'More Info' I see this:

Canonical does not provide updates for GNOME Shell. So, it is not Canonical's responsibility. And as to the issues that Canonical have with the Gnome organisation, then read this:

[http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html#more]("http://www.webupd8.org/2012/11/ubuntu-1304-only-some-gnome-components.html#more")

Think of this for a moment. If Ubuntu had stuck to Gnome 3 and Gnome 3 shell and not brought in Unity, all of us would be experiencing the buggy Gnome Shell experience that you people are having.

Regards.

---

### Post by grege on 2012-11-04
> **Phaze08 said:**
> 
Also, when I get system notifications, those new ones in shell v 3.6.1, it just pops up right in the center of the screen, except instead of the notification, its just the app icon, and when I click, it just goes away and nothing else happens lol. 
Anyone else having these issues?

This is the fault of a dud theme, the author made the notification area too narrow. Not all themes marked 3.6 are good. The solution is simple. Try standard theme, if it works then find a new theme that also works.

---

### Post by grege on 2012-11-04
BTW. If you do a clean install using UGR (Ubuntu Gnome Remix) as your base and just use Gnome then you should have a reliable desktop. Add the Gnome PPA and update to all the latest Gnome components like Nautilus 3.6 and get a "proper" Gnome experience. Find good themes, not just any old theme.

If you just add Gnome Shell to a standard Unity based install then you end up with a half hearted hybrid.

My Gnome 3.6 is rock solid.

---

### Post by markbl on 2012-11-04
> **grege said:**
> 
If you just add Gnome Shell to a standard Unity based install then you end up with a half hearted hybrid.
I have not tried 12.10 yet but that is certainly not true on 12.04. I have been using Gnome shell on stock Ubuntu 12.04 all day every day and it has always been rock solid, much more so than Unity. Performance has always been better also.

---

### Post by grege on 2012-11-05
> **markbl said:**
> I have not tried 12.10 yet but that is certainly not true on 12.04. I have been using Gnome shell on stock Ubuntu 12.04 all day every day and it has always been rock solid, much more so than Unity. Performance has always been better also.

I do not disagree. In 12.10 you can just add Gnome Shell to a stock install and it will work and it should be stable.

Unfortunately in 12.10 they have decided to hold back versions of Gnome components for the benefit of Unity. I have just added shell to a stock install and it works fine, but some bits are 3.6 and others are 3.4. It was stable, but a hybrid of versions. My point is that if you want to be a pure Gnome user, Ubuntu Gnome Remix plus the Gnome PPA is the best approach. I think the problems listed above are caused by other factors, mostly themes and the fact that the extensions take a while to catch up when a new version comes out.

:)

---

### Post by markbl on 2012-12-30
> **grege said:**
> 
Unfortunately in 12.10 they have decided to hold back versions of Gnome components for the benefit of Unity. I have just added shell to a stock install and it works fine, but some bits are 3.6 and others are 3.4. It was stable, but a hybrid of versions. My point is that if you want to be a pure Gnome user, Ubuntu Gnome Remix plus the Gnome PPA is the best approach. I think the problems listed above are caused by other factors, mostly themes and the fact that the extensions take a while to catch up when a new version comes out.
To follow up on this and my post above, it is 8 weeks later and I have installed a fresh 12.10 Ubuntu (64 bit) install on new hardware and using gnome shell and the gnome 3 ppa. I also find the gnome-shell a little buggy. Been using it for about a week now and have had quite a few complete desktop lockups. This did not happen with 12.04.

---

### Post by fantab on 2012-12-31
Ubuntu chose UNITY over Gnome-Shell for a reason. Ubuntu/Canonical does not support Gnome-Shell. Like many posts here mention, install Ubuntu-Gnome-Remix. Yes we can use Gnome-Shell on default Ubuntu by removing Unity and installing GS through adding a dedicated ppa BUT we have to remember that Ubuntu may or may not gel with GS... I don't think it was even tested to do so. 

However, Ubuntu-Gnome-Remix is designed to work with Gnome-Shell, so unlike Ubuntu, UGR goes well with GS. IMO Fedora works best with Gnome-Shell. GS is a default in Fedora. My general observation has been that Distros work best with their default Desktops.

I hope we make an informed choice in the future. 

My two cents....

---

### Post by markbl on 2012-12-31
> **fantab said:**
> Ubuntu/Canonical does not support Gnome-Shell. Like many posts here mention, install Ubuntu-Gnome-Remix. Yes we can use Gnome-Shell on default Ubuntu by removing Unity and installing GS through adding a dedicated ppa BUT we have to remember that Ubuntu may or may not gel with GS... I don't think it was even tested to do so.
You are wrong on many fronts.
[LIST]
[*]Ubuntu provide gnome shell as a standard package so they do support it.
[*]You don't have to uninstall Unity or any other Ubuntu software, gnome-shell happily exists as an alternative session option on the Ubuntu login screen.
[*]You don't need to add any ppa's to install gnome shell.

[*]The ubuntu team that created gnome remix have stated that it is essentially the same as installing gnome-shell from the standard packages.
[/LIST]
I have long used gnome shell (and unity) on Ubuntu 11.10 and 12.04 and it has always been more reliable and far less buggy than unity.

Now, I actually tried to install gnome remix this time but the installer ISO (12.10.1 64 bit) would not boot from a USB stick on my system. I remade the image several times, tried 3 different USB sticks, verified the checksum, etc. Then I tried booting with the stock ubuntu 12.10 image and it worked fine. There seems to be a bug on that gnome remix image with my system. 12.10.1 was supposed to fix this for EFI systems but it seems still to have a bug.

Anyhow, I am still quite happy with gnome shell on ubuntu 12.10, my point here was just that I agree with the OP that it has some bugs, at least compared to 12.04.

---

### Post by fantab on 2012-12-31
> **markbl said:**
> You are wrong on many fronts.
[LIST]
[*]Ubuntu provide gnome shell as a standard package so they do support it.
[*]You don't need to add any ppa's to install gnome shell.
[/LIST]

Thanks markbl for correcting me regarding NOT adding any additional ppa to install gnome-shell. I personally haven't installed GS but have friends who have... 

Fedora with gnome-shell is a different experience than Ubuntu and gnome-shell. I attribute this difference to Ubuntu-team's disinterest with gnome-shell. Supported officially or not.

My two cents...

---

### Post by Rasa1111 on 2013-01-29
> **Phaze08 said:**
> I've been a good fan of gnome-shell for a long time. I've been using it since it came around not long ago and I just love the extensions, themes, and speed of it. Ever since I upgraded though, its pretty buggy. 
First, when I enable user themes, and I press super key to show open windows, the shell crashes. 
Second, all my extensions disable every time I log in (I've updated the ones that are available on extensions.gnome.org)
Also, when I get system notifications, those new ones in shell v 3.6.1, it just pops up right in the center of the screen, except instead of the notification, its just the app icon, and when I click, it just goes away and nothing else happens lol. 
Anyone else having these issues?

On a side note, anyone know a good app to replace Ubuntu Tweak since its been discontinued?


Gnome Shell is super buggy for me in ubuntu 12.10 also. 
It worked pretty flawlessly in my 12.04 install..
but ive not been able to use gnome shell for more than 5 minutes in 12.10 without something messing up. 

Also.. Ubuntu tweak is not discontinued..
The new version is pretty awesome actually. :)

---

### Post by M4he on 2013-01-30
I also experienced some issues using Gnome Shell (ubuntu-gnome-desktop) beneath Unity, even after replacing lightdm with gdm. It just wasn't very stable. Sometimes the menu options for shutting down just disappeared and things like that. So I did the following:

[LIST]
[*]Downloaded Ubuntu 12.10 minimal CD image
[*]installed the core system via the text based installer
[*]chose "manually select packages" instead of installing a whole DE
[*]installed a gnome-shell environment via:
[/LIST]
```
apt-get install --no-install-recommends ubuntu-gnome-desktop
```(the --no-install-recommends switch is to prevent the system from  getting bloated right from the start and only install necessary packages except the optional ones)
and then manually installed all desired applications and packages via synaptic.

[SIZE=2]The result is a blazingly fast and so far stable Gnome Shell environment free from any Unity remnants.[/SIZE]


There is only one issue: when I go into the system settings, try to add a Google account to "online accounts" and authorize it via Google an additional authorization dialog pops up in GS (looking like the password request) and asking me for my Google account password. The problem is, neither the cancel nor the confirm button in this dialog work, leaving me stuck at the prompt screen. Only reboot or gdm restart helps. 
I experienced this on the latest 3.6 GS on Arch Linux as well, so it doesn't seem to be Ubuntu exclusive. However, on Fedora 18's GS it does work, despite they are using 3.6 as well.
Don't know if I'm just missing a package here or if it is a bug...

---


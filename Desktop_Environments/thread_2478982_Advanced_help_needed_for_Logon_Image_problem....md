---
title: "Advanced help needed for Logon Image problem..."
date: 2022-09-10
forum: Desktop Environments
---

### Post by MAFoElffen on 2022-09-10
Any 'Exterminators' here? (Will explain. LOL)

A few might know me here from other sections. With years of experience comes "bigger problems" when you dig down and play...

Summary when the problem occurred: Installed XCFE desktop alongside other desktops, and the Iconic "Rodent" logon background image has taken over... And I can't get rid of it!!!

Background: (Not a pun). Since I support Ubuntu and most it's Flavors, I install many desktops alongside each other... Though I exist (work) mostly within Gnome and i3. I like to tweak my UI's to make them my own. For plymouth, I use the Ubuntu Rising Sun. For my Login screen, I use a blueish metal hexagonal grid as a logon background. For my DM I use lightdm (preferred) or lightdm-gtk-greeter (second choice). For my DE's my first choice is Gnome 3x (1st choice) or i3 (secondary choice), with the Black metal hexagonal grid Background from Solaris 11, which I redid for 1920x1080... The overlaid on my background, is my own written Conky 'System Status' widget... And an Arctic Dark theme.

But now, with my main workstation, I have that pest/rodent problem that I am hitting my head on, trying to rid myself of it... Even if I switch the DM to LightDM-Gtk-Greeter, and set the background in /etc/lightdm/lightdm-gtk-greeter.conf... I can see the my grid come up, then at the last second, the rat(mouse) appears...

---

### Post by tea for one on 2022-09-11
No More Mr Mice Guy (apprentice pest controller) reporting for duty.

As lightdm is misbehaving for you at the moment, perhaps switch to gdm3 and add this [https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background](https://github.com/PRATAP-KUMAR/ubuntu-gdm-set-background)
The github page does not explicitly mention 22.04 but line 27 of the script mentions
```
Script is only for Ubuntu ${BWhi}20.04, 21.04, 21.10 & 22.04${Red} Only
```
I've been using it for more than a year in both Ubuntu 20.04 and 22.04
More info [https://www.omgubuntu.co.uk/2022/01/change-ubuntu-login-screen-background](https://www.omgubuntu.co.uk/2022/01/change-ubuntu-login-screen-background)

---

### Post by &amp;KyT$0P# on 2022-09-11
> **MAFoElffen said:**
> Even if I switch the DM to LightDM-Gtk-Greeter, and set the background in /etc/lightdm/lightdm-gtk-greeter.conf... I can see the my grid come up, then at the last second, the rat(mouse) appears...

This sounds to me like you have not disabled the "Use user wallpaper if available" option.  A snippet from my [FONT=Courier New]/etc/lightdm/lightdm-gtk-greeter.conf[/FONT] , under [FONT=Courier New][greeter][/FONT] section -
```
user-background = false
hide-user-image = true
```

> For my DM I use lightdm (preferred) or lightdm-gtk-greeter (second choice).

:confused:
This is like saying '*For my windowing system I use X11 (preferred) or Openbox (second choice)*.'

What LightDM greeter is your first choice?  Does it have an equivalent of the "Use user wallpaper if available" option?

> **tea for one said:**
> As lightdm is misbehaving for you at the moment, perhaps switch to gdm3 

In my experience Xfce is not quite fully compatible with gdm3, this combination gave me screen lock issues.

---

### Post by tea for one on 2022-09-11
> **halogen2 said:**
> In my experience Xfce is not quite fully compatible with gdm3, this combination gave me screen lock issues.
Yes, I completely agree if XFCE was the only desktop.

Multiple desktops in play and first choice is gnome3.

---

### Post by MAFoElffen on 2022-09-13
> **halogen2 said:**
> This sounds to me like you have not disabled the "Use user wallpaper if available" option.  A snippet from my [FONT=Courier New]/etc/lightdm/lightdm-gtk-greeter.conf[/FONT] , under [FONT=Courier New][greeter][/FONT] section -
```
user-background = false
hide-user-image = true
```

LMAO!!! I changed those to lines to that... And the Jammy Jellyfish showed up (Instead of mine), then the mouse took over again. It's in the CSS somewhere. I'm just stuck remembering where... Thank you for the try and idea on that...
> **halogen2 said:**
> 
:confused:
This is like saying '*For my windowing system I use X11 (preferred) or Openbox (second choice)*.'

I said what I said. They are different packages. They are both Display Managers / Graphical Logins that look the same but have different underpinnings.

If you want to say why I would compare a graphics engine to a basic Windows Manager? Then I lose your reference... Maybe you could explain that reference and why you think they are so different...

Because on your other comment, we have spoken before. Feel out your audience first. Remember I have been using and supporting  XServer for 32 years... And (LOL) my Ama-Gi Project's LiveCD, I still  use OpenBox for it's DE... Using minimal X and no Graphical Login Manager at all... I've been supporting the Linux Graphics  Layers for 15 years, since Alan Coopersith taught me what I needed to know dealing with it on desktops. I know the differences in the pieces... But it's  been about 4 years since I've dealt with where things are in Lightdm. Since then, there are geresource files.
> **halogen2 said:**
> 
What LightDM greeter is your first choice?  Does it have an equivalent of the "Use user wallpaper if available" option?
My first choice is the classic, standard Lightdm package... Except there is no conf file for that. And I forget where the css file for it is. It's been a while and they have change things again.

GDM? No. I have it installed, but do not like it, and XFCE doesn't like it. Yes, I know the commands from that script.

I like the look and feel of LightDM for a DM. I hate Wayland as a graphics engine. X11 is my choice for a graphics engine.

Background--  Even though I have various pieces and desktops loaded, where I can easily just switch to... That is not what I am here to discuss or debate. I have those installed "as multiples", because when I test my scripts or when I am supporting contributions to others (such as boot-repair) or supporting users directly... I test my solutions before telling User's that "this works". I don't do that *blindliy*. (I test that first.) My other computers are not setup that way. And no, I am not your normal Linux user.

---

### Post by &amp;KyT$0P# on 2022-09-13
> **MAFoElffen said:**
> I lose your reference... Maybe you could explain that reference and why you think they are so different...

Apologies for being unclear, I just thought that was a good analogy (lightdm-gtk-greeter is to LightDM login screen approximately what Openbox is to X11 windows).  Didn't mean to offend :oops: Just got confused when you called lightdm-gtk-greeter a display manager.

> My first choice is the classic, standard Lightdm package...

I have never got LightDM to work without explicitly installing a greeter.  If you're saying LightDM has a built-in greeter and that's what you prefer to use, how to enable this so I can test this out?

---

### Post by MAFoElffen on 2022-09-13
I just removed XFCE4, XFWM4 and GDM3... LightDM is still there, but it will not show. Whatever is the low-res DM for XFCE4 is still there and will not go away or let it change to LightDM.

Whatever DM installed as a dependency to XFCE "took over" as the DM/Login Manager. Which is strange. LightDM says it's there. 'lightdm-gtk-greeter' is there and I can see changes to it take effect underneath, before whatever that XFCE style graphicl Login Manager overlays over it...

This is where I'm stuck...

Edit--
On my other machines, i install themes manually. I don't install a greeter for LightDM. I change the actual css for the background... (somewhere in /usr/share/themes/) But I honestly haven't done the last machine before this in about a year, so I don't remember which css file I edited. And on those other machines, I hadn't installed XFCE on them...

EDIT2-- 
I guess I could spin up a couple VM to see the dependencies XFCE4 wants to install when installed on a Vanilla minimal Desktop. I just thought someone might know without doing that.

---

### Post by &amp;KyT$0P# on 2022-09-13
> **MAFoElffen said:**
> I change the actual css for the background... (somewhere in /usr/share/themes/) But I honestly haven't done the last machine before this in about a year, so I don't remember which css file I edited. 

Would [FONT=Courier New]debsums[/FONT] help you figure out which file it was?

---

### Post by MAFoElffen on 2022-09-13
I have not used 'debsums'... How do you think that might help me?

Oh... To answer one of your previous questions. The default greeter for the standalone LightDM package is 'untity-greeter'. I saw it during my VM Test recreating it.

During the test case I installed everything except XFCE4. Then I made a list of the additional dependencies that would be installed with xfce4 and made it into a list into a file. Then wrote a script to  read that, loop through, and remove them...

The attachment is where I'm at now. With GDM3 there or not, with LightDM there, it's still stuck on that same login artifact. I can't change it to GDM3 or LightDM.

---

### Post by MAFoElffen on 2022-09-14
Here is the machine and it's settings (from the UbuntuForums 'system-info' script: [https://paste.ubuntu.com/p/s7jjJj6Hz2/](https://paste.ubuntu.com/p/s7jjJj6Hz2/)

If you look in the Graphics Environment Section, the default DM setting in '/etc/X11/default-display-manager' is set to LightDM... But that Login Widget , left over from *somewhere* is still there.

To me, it looks like an XDM login widget. If I query for that, this is the output...
```

mafoelffen@Opti-Ubuntu-Main:~/Scripts$ apt list xdm
Listing... Done
xdm/jammy 1:1.1.11-3ubuntu2 amd64

```
Wait one.... If I try to remove it, apt says it is not installed.

I see some problems. Not sure if it is related. Apt now points to a snap version for gnome-sessions (see User Installed Section and Snaps Section). if I search for the location of 'unity-greeter', it shows up both in the traditional location and in Snap directories... Which also no longer populates the Environment Variables for $XDG_CURRENT_DESKTOP and $CURRENT_SESSION... Also, Arc theme is applied, but 'gsettings get org.gnome.desktop.interface gtk-theme' is reporting that 'Adwaita' theme is current(?)...
 
Hmmm. Thinking. Those are sideline issues. [COLOR=#FF0000]The main issue right now is getting rid of this login widget so that GDM3 and LightDM work normally again.[/COLOR]

---

### Post by &amp;KyT$0P# on 2022-09-14
> **MAFoElffen said:**
> I have not used 'debsums'... How do you think that might help me?

If the CSS file you modified is in /usr/share/themes it is likely part of a .deb package, and debsums could show you which files of .deb packages were modified.

> To answer one of your previous questions. The default greeter for the standalone LightDM package is 'untity-greeter'.

Thanks.  I installed unity-greeter in my Xubuntu 22.04 with
```
sudo apt-get --no-install-recommends install unity-greeter
```
and was able to select it by creating a file [FONT=Courier New]/etc/lightdm/lightdm.conf.d/greeter.conf[/FONT] -
```
[Seat:*]
greeter-session=unity-greeter
```

Rebooted for this to take effect.

Then, to disable using user background image and choose a non-default background image -
```
pkexec --user lightdm sh -c "DISPLAY=$DISPLAY gsettings set com.canonical.unity-greeter draw-user-backgrounds false"
pkexec --user lightdm sh -c "DISPLAY=$DISPLAY gsettings set com.canonical.unity-greeter background /usr/share/backgrounds/ubuntu2_by_arman1992.jpg"
```

If I'm understanding correctly, the result I got at this point is what you're trying to achieve.

Does this help?

> The attachment is where I'm at now. With GDM3 there or not, with LightDM there, it's still stuck on that same login artifact.

That looks to me like lightdm-gtk-greeter

---

### Post by ajgreeny on 2022-09-14
I am late to this thread but I do use Xubuntu (Xfce) which uses lightdm and with Xubuntu you have a configuration dialogue from command ***lightdm-gtk-greeter-settings-pkexec*** which allows you to set a specific image as the background or simply choose the wallpaper you have chosen for the desktop as well as the ***.face*** image that may be available in your home.

I note that lightdm-gtk-greeter-settings is not a dependency of ***lightdm*** or ***lightdm-greeter*** so you may not have it installed. I am also assuming that the settings you make in that will work in all DEs that you may want to use.

Sorry if I've misunderstood the original query.

---

### Post by MAFoElffen on 2022-09-14
> **halogen2 said:**
> 
Thanks.  I installed unity-greeter in my Xubuntu 22.04 with
```
sudo apt-get --no-install-recommends install unity-greeter
```
and was able to select it by creating a file [FONT=Courier New]/etc/lightdm/lightdm.conf.d/greeter.conf[/FONT] -
```
[Seat:*]
greeter-session=unity-greeter
```
Rebooted for this to take effect.

Wahoo! (Sort of... LOL) This got me good on displaying the LightDM style Unity Greeter again. 
*** That file did not exist, so I created /etc/lightdm/lightdm.conf.d/50-unity-greeter.conf' new with these lines:
```

[SeatDefaults]
greeter-session=unity-greeter

```
 ...and restarted the Lightdm service with
```

sudo service lightdm restart

```
which restarts lightdm without a reboot. Lot's faster on that, as it is server hardware and takes forever to get through it's post processes.

That was what got LightDM working for me again!!! Could you please post yours so I have the whole file. Please, please, please! 

I did lose my background again, even with the following from your suggestions:
> **halogen2 said:**
> 
Then, to disable using user background image and choose a non-default background image -
```
pkexec --user lightdm sh -c "DISPLAY=$DISPLAY gsettings set com.canonical.unity-greeter draw-user-backgrounds false"
pkexec --user lightdm sh -c "DISPLAY=$DISPLAY gsettings set com.canonical.unity-greeter background /usr/share/backgrounds/ubuntu2_by_arman1992.jpg"
```

This part did not work. It just kept at the Jammy-Jellyfish background. I went back with 'dconf.editor' and checked that setting... It took mine, '/usr/share/backgrounds/BlueGrid_wallpaper.png', and the other was set to false, but my background wasn't showing at all in the LightDM panel. As a test... If I renamed mine as it, it showed, but that is a hack.

@ajgreeny - My preference is using the Unity Greeter. For lightdm-greeter-gtk, I am assuming that the lightdm-gtk-greeter-pkexec settings dialog edits the '/etc/lighdm/lightdm-gtk-greeter.conf' file, which I was editing directly.

---

### Post by &amp;KyT$0P# on 2022-09-14
> **MAFoElffen said:**
> Could you please post yours so I have the whole file. Please, please, please! 

The two lines are the entire file, I also created it new specifically for this.

> This part did not work. It just kept at the Jammy-Jellyfish background. I went back with 'dconf.editor' and checked that setting... It took mine, '/usr/share/backgrounds/BlueGrid_wallpaper.png', and the other was set to false, but my background wasn't showing at all in the LightDM panel.

Sorry I have no more ideas :( the commands I posted work for me as does changing those settings in dconf-editor -
```
pkexec --user lightdm sh -c "DISPLAY=$DISPLAY dconf-editor"
```

---

### Post by MAFoElffen on 2022-09-15
Epitath-

@halogen2 - Thank you very much for your help. 

This is what I did additional to what we both said... in '/etc/lightdm/lightdm.conf.d/
```

[Seat:*]
greeter-session=unity-greeter

[org.gnome.desktop.background]
picture-uri='file:///usr/share/backgrounds/BlueGrid_wallpaper.png'

[org.gnome.desktop.session]
session-name="ubuntu"

[com.canonical.unity-greeter]
draw-grid=false
draw-user-backgrounds=true

```
Your  tag was correct. [SeatDefaults] was deprecated and replaced by [Seat:*]  in 15.10. I did both key=values and still failed, but did my hack for  now. 

Having to get back to some DEV work... The "main complaint  was that I couldn't get LightDM working. Your fix on getting LightDM to  work for me works. So closing this out as "SOLVED". Thank you again.

On anything else, I'll pursue later. That workstation is a very complex config.I'll trace that down later...

---

### Post by &amp;KyT$0P# on 2022-09-15
You're welcome. :KS

---


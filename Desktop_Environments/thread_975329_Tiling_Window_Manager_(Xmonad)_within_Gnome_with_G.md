---
title: "Tiling Window Manager (Xmonad) within Gnome with Gnome Do"
date: 2008-11-08
forum: Desktop Environments
---

### Post by brunovecchi on 2008-11-08
I'd like to share how to **configure Xmonad to fit nicely in Gnome **(replacing metacity as the window manager) and, as a plus, to be able to use **Gnome Do** as a launcher as well.

This implies that you'll have the complete Gnome Desktop Environment (menus, taskbar, panels with clock, notification area, themes, fonts, wallpapers, etc) but with the advantage of having Xmonad as your window manager.
I attached some screenshots of how it looks.

**Step 1: Installation**

First of all, you'll need to have xmonad and xmonad-contrib packages installed:
[LIST=1]
[*] xmonad
[*] libghc6-xmonad-dev
[*] libghc6-xmonad-contrib-dev
[/LIST]

If you are running Intrepid, all this packages are updated and work fine. If you are running Hardy, you'll have to include Intrepid main in your sources to access the updated libghc6-xmonad-contrib-dev package, which has the Gnome config file that allows Xmonad to play nicely with Gnome.

Edit your /etc/apt/sources.list and include the following line:

```
  # Intrepid sources
  deb http://archive.ubuntu.com/ubuntu intrepid main universe
```

Now update your sources file and install the xmonad and xmonad-contrib packages listed above. You can disable the Intrepid packages later if you do not need/want them.

You should now have xmonad installed. if you want to test it, you can log out of your session and log in again selecting xmonad in the GDM screen. You'll note that there are no panels, no background, etc. If you try to launch anything (alt+shift+enter launches a terminal, you can launch applications from there), the gtk theme won't be the one you probably have in gnome, etc. We'll have to tweak things a little to change all that.

**Step 2: Replacing Metacity**

To override metacity when logging in to gnome, create a file name .xsession in your home folder with the following content:

```
  export WINDOW_MANAGER=xmonad
  exec gnome-session --purge-delay=3000
```

**Step 3: Tweaking Gnome** **[COLOR="Red"]Not necessary![/COLOR]**

You'll have to disable the desktop (this means you'll have no desktop icons, wich don't make much sense with a twm anyway). Type this in the command prompt:

```
  gconftool-2 --type boolean --set /apps/nautilus/preferences/show_desktop false
```

**[COLOR="Red"]This step is not mandatory! You could do it anyway if you feel like it, but I found out that you can have your beloved desktop icons, it works anyway.[/COLOR]**

**Step 4: Tweaking Xmonad**

Create the directory .xmonad in your home folder, and the file xmonad.hs within it. Add the following lines:

```

import XMonad
import XMonad.Config.Gnome

main = xmonad gnomeConfig

```

Save it and restart the X session normally. That's it!

**Step 5 (Optional): Further tweaking for Gnome Do**

If you are a Gnome Do user (and you should be!), you'll notice that Xmonad tries to handle Do's window like a regular one, resizing it to full screen. The following xmonad.hs file make it ignore Do's existence:

```

import XMonad
import XMonad.Config.Gnome
import XMonad.ManageHook

myManageHook :: [ManageHook]
myManageHook = 
    [ resource  =? "Do"   --> doIgnore ]

main = xmonad gnomeConfig
    { manageHook = manageHook gnomeConfig <+> composeAll myManageHook }

```

That should do the trick. You can also edit that config file to further customize it (focused window border color, for instance). Check out the [**_Xmonad page_**]("http://xmonad.org/")

I suggest you also add [**Vimperator**]("http://vimperator.org/trac/wiki/Vimperator") to the mix (It's a Firefox addon that enables you to use vim-like keybindings for web browsing); you'll have a full-featured and keyboard driven working environment!

For a more comprehensive guide, visit the following page: [**http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome**]("http://http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome")

---

### Post by chucky chuckaluck on 2008-11-08
great idea. i have a few questions...
could one also start gnome and then do F2 *xmonad --replace* (is that the right command?)? and for those using a transparent gnome-terminal, would using something like feh to set the wallpaper, still work? (can't see why it wouldn't, but i've not used gnome much.)
also, would switching workspaces still work as it normally does in xmonad?

---

### Post by brunovecchi on 2008-11-08
> **chucky chuckaluck said:**
> great idea. i have a few questions...
could one also start gnome and then do F2 *xmonad --replace* (is that the right command?)? 



about xmonad --replace, I don't know if it'll work. This will surely do:

```
killall metacity && xmonad
```

However, I think that creating the .xsession file is better, because this way you don't have to load metacity and then replace it with xmonad, you just load xmonad directly.

>  and for those using a transparent gnome-terminal, would using something like feh to set the wallpaper, still work? (can't see why it wouldn't, but i've not used gnome much.)


You don't need to use feh as a wallpaper, since gnome already handles it. If you use compositing for transparency, you should be able to see your background without using feh. You also change it the same way you'd change it in standard metacity gnome (via system->preferences).

>  also, would switching workspaces still work as it normally does in xmonad?

Switching workspaces will work just as it does with xmonad (via mod+number, or whatever you set it to in the config files). If you want the metacity keybindings, you should change them in the config file.

Also, for changing focus between windows, both gnome (alt+tab) and xmonad (mod+j or mod+k) keybindings will work

---

### Post by chucky chuckaluck on 2008-11-08
i thought nautilus handled the wallpaper in gnome. that's why i wondered about what one would use instead. 
what you say about not starting metacity in the first place, is indeed preferred.

---

### Post by brunovecchi on 2008-11-08
> **chucky chuckaluck said:**
> i thought nautilus handled the wallpaper in gnome. that's why i wondered about what one would use instead. 


Yes, it does! But we are not disabling nautilus here, just setting it to not show the desktop icons via gconf-editor. Wallpaper is displayed nonetheless.

---

### Post by chucky chuckaluck on 2008-11-08
> **brunovecchi said:**
> Yes, it does! But we are not disabling nautilus here, just setting it to not show the desktop icons via gconf-editor. Wallpaper is displayed nonetheless.

ah, i see. i guess i had it mixed up with using nautilus in openbox, etc.

---

### Post by zmjjmz on 2008-11-08
This isn't exactly working out for me:
What happens is that whenever I open a window it just sits in the top left corner (not maximized) and none of the normal xmonad keybindings work....
Anyone know what I'm doing wrong?

EDIT: Ok, I'm pretty sure xmonad just isn't running.
Which is totally the case.
I'd worry about it not autostarting if I ever find myself having to logout often, but with this thing's extreme stability...

---

### Post by brunovecchi on 2008-11-10
> **zmjjmz said:**
> This isn't exactly working out for me:
What happens is that whenever I open a window it just sits in the top left corner (not maximized) and none of the normal xmonad keybindings work....
Anyone know what I'm doing wrong?

EDIT: Ok, I'm pretty sure xmonad just isn't running.
Which is totally the case.
I'd worry about it not autostarting if I ever find myself having to logout often, but with this thing's extreme stability...

Have you solved your problem? If not, could you describe it further?
For it to replace metacity, logging out and back in should do (Ctrl+Alt+Backspace).
After changing xmonad's config file, just press Alt+Q and it will reload, no need to restart X.

Side note: I also noted that it is not mandatory to disable desktop icons! So really there is nothing to lose here, it's a clean replacement for metacity!

---

### Post by theDaveTheRave on 2008-11-10
Hi all

Ive added xmonad and first impressions are that I like what I see!

I have some issues with keybindings however.

I can get a terminal, and from here I can run whatever packages I want. Howeve that means that every open window is taking up 2 processes, which to me seems excesive!

How do I get a <menu> of some sort to pop up?? I've tried all the various suggested keybinding (such as <mod1 p> or on my terminal <alt p> but nothing shows up?

I can confirm that certain other binding work, such as <alt ,> to shrink the size of the active window - it is this that appeals to me in fact.

so my question is realy how do I get to set my keybindings, and also set some of my extra keys that I used to use in gnome? I have a mail, web and others that I had bound to certain stuff, and I'd like to keep them, if poss.

Oh and I have a problem with java applications, a big thing as I'm a Java developer!

Thanks in advance

Dave

---

### Post by mrgnash on 2008-11-10
Nice idea, but it doesn't work for me. Xmonad starts, but it doesn't actually load properly:

```
xmonad: X11 error: BadAccess (attempt to access private resource denied), request code=2, error code=10
```

---

### Post by brunovecchi on 2008-11-10
> **mrgnash said:**
> Nice idea, but it doesn't work for me. Xmonad starts, but it doesn't actually load properly:

```
xmonad: X11 error: BadAccess (attempt to access private resource denied), request code=2, error code=10
```

According to the [**XMonad mailing list**]("http://www.haskell.org/pipermail/xmonad/2007-June/001285.html"), this issue arises when X has already loaded a window manager.

Have you created a ".xinitrc" file in your home folder with the appropiate command to launch xmonad and no other window manager? Hope it helps!

---

### Post by brunovecchi on 2008-11-10
> **theDaveTheRave said:**
> Hi all

Ive added xmonad and first impressions are that I like what I see!

I have some issues with keybindings however.

I can get a terminal, and from here I can run whatever packages I want. Howeve that means that every open window is taking up 2 processes, which to me seems excesive!

How do I get a <menu> of some sort to pop up?? I've tried all the various suggested keybinding (such as <mod1 p> or on my terminal <alt p> but nothing shows up? 

Well, you could use dmenu (package dwm-tools or something like that). This will allow you to launch apps via mod+p. However, if you followed the guide above, mod+p should open gnome-launcher. Have you tried following the steps above, or are you just trying XMonad alone?

>  Oh and I have a problem with java applications, a big thing as I'm a Java developer! 

Yes, there's a workaround for that. You have to add this line to your $HOME/.profile file:

```

export AWT_TOOLKIT=MToolkit

```

AFAIK, this is due to a Java problem, and it's said to be solved for the latest java versions.

---

### Post by theDaveTheRave on 2008-11-10
> **brunovecchi said:**
> Well, you could use dmenu (package dwm-tools or something like that). This will allow you to launch apps via mod+p. However, if you followed the guide above, mod+p should open gnome-launcher. Have you tried following the steps above, or are you just trying XMonad alone?

AH that could be where I have gone wrong.... in my keeness to try XMonad I may have missed a step :rolleyes:


> 
Yes, there's a workaround for that. You have to add this line to your $HOME/.profile file:

```

export AWT_TOOLKIT=MToolkit

```



I did find this work around, but I wasn't entirely sure where I should put the code line, so you have solved this issue for me... I hope

> 
AFAIK, this is due to a Java problem, and it's said to be solved for the latest java versions.


Hmm?? it still seems to be an issue in my distro, I a, however running intrepid, so it could be an issue with a broken Ibex? or just the version in the repositories.... I'll get back with the success/failure or it in my distro.

Dave

---

### Post by K.Mandla on 2008-11-10
Moved to Desktop Environments.

---

### Post by theDaveTheRave on 2008-11-12
hello again.

so I checked a few things and made sure I had copied all the required files.

I can now confirm the following.

i get an error each time I log into XMonad stating that composeAll is out of scope?

I assume that this means something needs importing somewhere, but what and where?

I also added the line for enabling java applications, and now I can't even open them in normal GNOME? so I removed the line from the .profiles file and can now open java stuff in GNOME but still not in XMonad.

I am still able to open a terminal or change the order of windowing etc, but still no menu via <alt p>, which is highly aggravating, as this means I have to open a terminal to log in and out!

And my boot up times are now ridiculously long! it seems as though it hangs part way through boot up, again this may be related to other intrepid issues.

am I able to open a menu via the terminal?? as I would like to alter my keybindings etc, and this may enable me to do so - or help me investigate other issues within XMonad that I am not able to get to via GNOME - such as switching virtual terminals and sending windows to specific terminals.

thanks again in advance.

Dave

---

### Post by DarthDevilous on 2009-02-18
> **brunovecchi said:**
> **Step 5 (Optional): Further tweaking for Gnome Do**

If you are a Gnome Do user (and you should be!), you'll notice that Xmonad tries to handle Do's window like a regular one, resizing it to full screen. The following xmonad.hs file make it ignore Do's existence:

```

import XMonad
import XMonad.Config.Gnome
import XMonad.ManageHook

myManageHook :: [ManageHook]
myManageHook = 
    [ resource  =? "Do"   --> doIgnore ]

main = xmonad gnomeConfig
    { manageHook = manageHook gnomeConfig <+> composeAll myManageHook }

```

I went one further and replaced the mod-p run dialog with Do. My config (adapted from the Config.Gnome module):

```

import XMonad
import XMonad.Config.Gnome
import XMonad.ManageHook
import qualified Data.Map as M

myManageHook :: [ManageHook]
myManageHook =
    [ resource =? "Do"   --> doIgnore ]

myKeys (XConfig {modMask = modm}) = M.fromList $
    [ ((modm, xK_p), spawn "gnome-do") ]

main = xmonad gnomeConfig
              { modMask = mod4Mask
              , manageHook = manageHook gnomeConfig <+> composeAll myManageHook
              , keys = \c -> myKeys c `M.union` keys gnomeConfig c
              }

```

---

### Post by oxsyn on 2009-02-22
Sick tutorial.  Exactly what I was looking for.  Thanks++ to the op.

---

### Post by rada on 2009-02-23
> **theDaveTheRave said:**
> I get an error each time I log into XMonad stating that composeAll is out of scope?

This is covered by 'import XMonad' are you maybe running an older version of XMonad than the ibex one? or only installed xmonad binary, not the libghc6-xmonad* stuff?

> **theDaveTheRave said:**
> 
I also added the line for enabling java applications, and now I can't even open them in normal GNOME? so I removed the line from the .profiles file and can now open java stuff in GNOME but still not in XMonad.

This [section from the XMonad FAQ]("http://haskell.org/haskellwiki/Xmonad/Frequently_asked_questions#Problems_with_Java_applications.2C_Applet_java_console") shows how to use setWMName in logHook of xmonad.hs (Config.Gnome uses EwmhDesktops extension, which makes this method rather than startupHook method necessary.)

> **theDaveTheRave said:**
> 
And my boot up times are now ridiculously long! it seems as though it hangs part way through boot up, again this may be related to other intrepid issues.
 The gnome-session --purge-delay=3000 line is supposed to help with that although I'm not sure ~/.xsession is actually getting read, still trying different things.

> **theDaveTheRave said:**
> 
am I able to open a menu via the terminal?? as I would like to alter my keybindings etc, and this may enable me to do so - or help me investigate other issues within XMonad that I am not able to get to via GNOME - such as switching virtual terminals and sending windows to specific terminals.

I was surprised to find I had to install gmrun for mod-shift-p to work, and dwm-tools for mod-p, but now we have the awesome example of how to set up gnome-do, so I don't really care so much. 

Still haven't worked out the right way to start gnome-settings-daemon, gnome-panel, etc. Rumoured .gnomerc doesn't seem to have installed on my ibex. I.e. when I choose session XMonad it's totally bare bones. With Config.Gnome as in your example running gnome-panel works sort of, but is obviously missing some other helper programs it needs, guess I need to search more.

---

### Post by falkaholic on 2009-03-02
Great stuff, exactly what I was looking for. 

I installed xmonad 8-1 from the ubuntu repositories. Using the import XMonad.Config.Gnome basic. 

It seem I'm not getting much of Gnome. There is not icons on the desktop (didnt turn them off), not status bar, etc. Seems to be basic xmonad.

I know xmonad is running with my xmonad.hs since it stops when I has an error in it. Speaking of errors, does anyone have a good no nonsense crash course in the haskell syntax?

---

### Post by oxsyn on 2009-03-08
Reformatted and reinstalled xmonad, using same instructions.  This time, however - I'm having a problem.

When I start xmonad up, my session is instantly killed, and I get a error message that ends with the following line:

** (gnome-session:6311): WARNING **: Unknown option --purge-delay=3000.

Now, if I hop back in on a different tty, I can remove that option from the OP's .xsession script.  It then loads.  But it's very, very unresponsive. 

When I try to open a new window, it takes upwards of 10-15 seconds.  Switching between windows takes 5+ seconds.  Resizing windows takes 5+ seconds.

What the heck is going on?

---

### Post by oxsyn on 2009-03-12
I'm not sure how, but it works now - with the --purge-delay=3000 delay line removed.

---

### Post by drcnoib on 2009-03-28
Unfortunately, can't reproduce the xmonad behavior... the desktop is not gone either... any suggestions (done everything as already done there).

Also, a suggestion for the thread creator: .xsession must be executable in order to be read. chmod +x .xsession  should do it (as i didn't have the .xsession file already created).

---

### Post by sam.bkh on 2009-04-01
Hi all,
I just tried to follow the instructions, running a pretty fresh install of 8.10 on my new Thinkpad x200 (only changes have been to get various pieces of hardware up and running). Installing xmonad works fine; I can start an xmonad session from the login screen without any trouble. I made the xmonad.hs file without trouble. When I made the .xsession file, things began to fall apart. When I logged in to gnome, I got an error. Here's my .xsession-errors from that attempt:

```
 /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

** (gnome-session:6767): WARNING **: Unknown option --purge-delay=3000
```

I followed the advice of the above poster and made .xsession executable with 

```
sudo chmod +x .xsession
```

Logged in, got another error. Here's the .xsession-errors file for this configuration:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/sam/.xsession: 2: exportrt: not found

** (gnome-session:7758): WARNING **: Unknown option --purge-delay=3000

```

No different. Since it didn't seem to be liking the last line of code, I got rid of it. Here's the .xsession-errors file from that attempt:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_CA.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/home/sam/.xsession: 2: exportrt: not found

```

I have no idea what this means. Since something about .xsession-errors didn't seem to be playing nice, I decided to test whether xmonad would run at all in gnome by logging in to gnome and then running

```
killall metacity && xmonad
```

Which has the following curious consequences: xmonad starts up, replacing metacity. All the keybindings seem to work fine, and the configuration for gnome (no gnome DO -- I need to start using that) works as well. The issue is that in the terminal in which I start xmonad, I get a constant stream of the following message:

```
Unknown ClientMessageEvent 246
```

If I ctrl+C out of it, xmonad stops and metacity starts again. Advice, please?

---

### Post by The_BB on 2009-08-04
> **sam.bkh said:**
> ```
/home/sam/.xsession: 2: exportrt: not found
```

I guess you've just got a typo in your .xsession. It's *export*, not *exportrt*.

---

### Post by spktkpkt on 2009-08-23
It is also possible (on Jaunty, i don't test it with older releases of Ubuntu) to set XMonad as default via gconf.
```
gconftool --type string --set /desktop/gnome/session/required_components/windowmanager gnome-wm
``````
gconftool --type string --set /desktop/gnome/applications/window_manager/current /usr/bin/xmonad
``````
gconftool --type string --set /desktop/gnome/applications/window_manager/default /usr/bin/xmonad
```You may have to change the path "/usr/bin/xmonad" ( you can get the path by typing **which xmonad** into your terminal ) to your binary. After that, logout and log back in (default Gnome session). Metacity should be replaced by XMonad.

You should configure XMonad to integrate nicely into Gnome **before** apply the strings.

To revert the changes, just replace "gnome-wm" by "metacity" and "/usr/bin/xmonad" by "/usr/bin/metacity" in the commands above.

---

### Post by Junkieman on 2009-10-18
I'm happily using Xmonad as my WM with gnome, on 8.10 Intrepid. The instructions from the OP gave the same error that Sam is seeing, so I rm'd the .xsession file and started over, following the instructions on the [Haskell Xmonad]("http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome#.gnomercgnome do") site -- adding a line to ~/.gnomerc

```
export WINDOW_MANAGER=xmonad
```

Perhaps the workaround for the OP has now been resolved by this time. It's working a sweet treat.

---

### Post by falkaholic on 2009-11-14
I seem to be having a bit a problem with xmonad and a clean install of 9.10.

Everything installs ok, and works fine when I do 'killall metacity && xmonad'

This issue is that none of these tricks seem set xmonad as my window manager. If I use the xmonad session selection from the login window, my session never starts. I just see my login background and nothing happens. 

Any tips?

---

### Post by linooks on 2009-12-12
@[falkaholic]("http://ubuntuforums.org/member.php?u=486123"):

What happens, if you enter alt + p?

If you use the xmonad session selection from the login window, you start xmonad without gnome. In this case, nothing seems to happen. but xmonad is already running.

My problem is, i can't start xmonad within gnome.

A .xsession file with:
```
export WINDOW_MANAGER=xmonad
exec gnome-session
``` starts a gnome-session with compiz nonetheless.

---

### Post by bjornbm on 2010-02-10
Re #28: you have to make gnome-wm the default window manager with the following command (from #25). gnome-wm will respect WINDOW_MANAGER but start compiz by default if WINDOW_MANAGER is not set.

```
gconftool --type string --set /desktop/gnome/session/required_components/windowmanager gnome-wm
```

---

### Post by poulter7 on 2010-08-10
If I recall:

```
[ resource  =? "Do"   --> _doIgnore_ ]
```

Is a bad solution as [FONT="Courier New"]doIgnore[/FONT] removes the gnome-do window from any window management, which when editing do plugins is terrifically unhelpful as mouse clicks don't register correctly.

Instead I use [FONT="Courier New"]doCenterFloat[/FONT]:
```

-- one of these imports is required?(!)
import XMonad.Hooks.ManageDocks
import XMonad.Hooks.ManageHelpers

[ className =? x -?> _doCenterFloat_    | x <- centerFloat  ]
where centerFloat = ["Do"]

```

Which produces the same effect but correctly windowing gnome-do, (with a center float). (Also you can list applications to window in the same way)

---


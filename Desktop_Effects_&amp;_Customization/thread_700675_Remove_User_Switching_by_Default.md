---
title: "Remove User Switching by Default"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by {}dif{} on 2008-02-18
Hi all,

I'm working on setting up a default configuration of Ubuntu at work and I'm down to the last couple issues that I need to resolve and they really concern the default desktop environment.

Most importantly, I need to remove Fast User Switching by default.  I tried Sabayon but it just crashed on me and I don't really even know where to start with editing the gconf directly.  I was able to remove the package but then an error displays when a new users profile is created when they log in for the first time that the applet can't be found.

So, where are the default configurations for the desktop stored?  And can anyone give some insights into how to remove the user switcher in that configuration?  While I'm at it, how do I add/remove Launchers to/from the panel by default?

Currently I have a script that installs all my default configurations after a clean install so I would prefer to do this by either copying over a text file from my script install source or running a sed command or redirect of some sort that adds or removes what needs to be done.  I can mostly figure that out later on my own time, I just want to make the point that doing something in the GUI afterward is not what I'm looking for.

Thanks in advance,

---

### Post by Sodki on 2008-02-22
As you mentioned, the real solution would be to use Sabayon. Unfortunately, as you also mentioned, Sabayon on Gutsy is totally unreliable. It crashes constantly and, when it doesn't crash, it doesn't save anything. It's a massive headache that has been reported **months ago** and wasn't fixed. I mainly use Ubuntu for professional reasons and Sabayon was a lifesaver... now I'm banging my head, because I can't work with my main tool.

---

### Post by chaos51 on 2008-03-12
I don't know if you got an answer to this but I was basically trying to do the same thing, I think I found a way.

I installed pessulus  
There are options in there to disable the user switching applet by just clicking a checkbox under disabled applets.

I think there is also an option to remove the fast user switching option from the screen save in pessulus as well.

---

### Post by chaos51 on 2008-03-12
I should add that I found some information about locking down gnome at the following:
[http://library.gnome.org/admin/deployment-guide/]("http://library.gnome.org/admin/deployment-guide/")

Hope that helps

---

### Post by {}dif{} on 2008-03-13
Thanks for the link.  I tried using pessulus and the GUI is nice but it created the xml file without any of the settings actually saved.  :-(

However, I did learn where to go from using pessulus so thank you.  I edited the xml file it created by adding some entries and attempting to use the same syntax as the other gconf files.  So this is what it looks like.

/etc/gconf/gconf.xml.mandatory/%gconf-tree:
```
<gconf>
        <dir name="apps">
                <dir name="gnome-screensaver">
			<entry name="idle_activation_enabled" type="bool" value="true">
			</entry>
			<entry name="idle_delay" type="integer" value="20">
			</entry>
			<entry name="lock_enabled" type="boot" value="true">
			</entry>
			<entry name="user_switch_enabled" type="bool" value="false">
			</entry>
                </dir>
                <dir name="panel">
                        <dir name="global">
				<entry name="disable_applets" type="string" value="OAFIID:GNOME_FastUserSwitchApplet">
				</entry>
                        </dir>
                </dir>
        </dir>
</gconf>
```

There's also a couple other settings that I want to apply but most importantly is the disable_applets and user_switch_enabled=flase settings.

However, this still isn't working for me.  I logged in on tty1 as root and removed my user home directory, then logged into gnome as my user and user switching was still there and the screensaver settings hadn't changed.

Any ideas?

Thanks in advance!

---

### Post by chaos51 on 2008-03-14
My problem was slightly different, basically if I tried to add the user-switching applet to the gnome-panel it would hang gnome and I'd have to CTRL+ALT+Backspace.  This still left the gnome-panel in the background so I'd have to CTRL+ALT+F1, login on a virtual console and manually kill gnome-panel before logging back into gnome.

I thought the best course of action would be to get rid of fast-user-switching (which I found out I couldn't because apt wants to remove ubuntu-desktop too).

So anyway, thats when I started to try and find a way to get rid of fast user switching.  Now, when I was in my console and looking at what was left after the crash, I noticed a process that looked something like:
/usr/libexec/fast-user-switch-applet-oaf-activate-iid=OAFIID:GNOME_FastUserSwitchApplet_Factory --oaf-ior-fd=29

So I went into gconf-editor and added OAFIID:GNOME_FastUserSwitchApplet_Factory to the list of disabled applets, I don't see that process anymore but I also don't know if that will help you or not.  

I'm also still trying to figure out other things, like how to get rid of the "Suspend" in the options menu on the login screen and also how to get rid of "Suspend" and "Hibernate" buttons on the "quit" menu in Gnome.  I did this before on dapper but I can't figure out how in Gutsy even though I think I made the correct setting changes in gconf-editor at least.

---

### Post by chaos51 on 2008-03-14
One other thing:
Did you try using gconf-editor
if you run it, look at:
/ -> app -> gnome-screensaver
   There is an option for "user_switch_enabled"

Don't know if that helps

---

### Post by {}dif{} on 2008-03-18
Thanks for all your help!

I realized that this is really threefold.  1, I needed to remove the applet and 2, I needed to remove it from the logout window and 3, I needed to remove it from the screensaver unlock dialog.

My previous post actually solved the first one but I had a syntax or spelling error in my file somewhere that I had to fix.  The second one was a completely different gconf key, /desktop/gnome/lockdown/disable_user_switching=true.  And thanks chaos51, the /apps/gnome-screensaver/user_switch_enabled=false fixed the last one.

All of these I set as mandatory settings through the %gconf-tree.xml file in /etc/gconf/gconf.xml.mandatory

Anyway, thanks for all your help!

---


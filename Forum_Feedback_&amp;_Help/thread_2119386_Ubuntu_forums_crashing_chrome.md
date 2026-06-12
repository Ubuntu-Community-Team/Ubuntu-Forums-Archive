---
title: "Ubuntu forums crashing chrome"
date: 2013-02-23
forum: Forum Feedback &amp; Help
---

### Post by r.stiltskin on 2013-02-23
I've been using google-chrome beta (v 25.0.1364.97 to be exact) for a few days without any problems until today when I used it to log into this forum.  As soon as I finish logging in and it begins to redirect away from the login page, all Chrome windows immediately crash.  None of that silly "snap" nonsense or any other indication of error.  Just gone.

Not just once -- I've logged in about 6 times now & this happens immediately every time.

This isn't happening on any other forum that I've logged into, or any other web pages.  Only here.  So what's up with that?

I'm running Xubuntu 12.04 32-bit with nouveau driver

---

### Post by nothingspecial on 2013-02-23
*Thread moved to **Forum Feedback & Help**.*

---

### Post by CharlesA on 2013-02-23
You could try creating a new profile for Chrome and/or trying to start it without any addons/extensions to see if the problem still occurs.

---

### Post by r.stiltskin on 2013-02-23
No extensions makes no difference.  And I deleted all ubuntu* cookies but it still crashes instantly.

Not sure what you're suggesting regarding a profile.

The only thing I can add is that now cprogramming.com forum is also crashing chrome.  Both use vbulletin.  Maybe an update to vbulletin was just installed and is causing this.

---

### Post by CharlesA on 2013-02-23
> **r.stiltskin said:**
> 
The only thing I can add is that now cprogramming.com forum is also crashing chrome.  Both use vbulletin.  Maybe an update to vbulletin was just installed and is causing this.

Doubt it, this forum hasn't been updated and works fine in Chrome for other members.

Try starting Chrome in safe mode, if it has one.

---

### Post by coffeecat on 2013-02-23
> **r.stiltskin said:**
> 
The only thing I can add is that now cprogramming.com forum is also crashing chrome.  Both use vbulletin.  Maybe an update to vbulletin was just installed and is causing this.

We have not had an update to vBulletin for nearly a year, but we are scheduled to upgrade to VB 4.2 in a few days time. The cprogramming forum is running 4.2.

I doubt VB is the problem here, but if you want to try some other VB forums to see if they cause the same issue, linuxforums.org, kubuntuforums.net, forums.opensuse.org and fedoraforum.org/forum/ all use vBulletin.

---

### Post by r.stiltskin on 2013-02-23
I've tried a bunch of forums using vbulletin, various versions including 4.2.0, 3.8.x and 3.7.x.  So far the only ones I found crashing chrome are this one and cprogramming.com.

I just realized that chrome-beta was updated this morning, so it must be something about that update.  But still, it's just these two forums.

edit:  I posted this issue on google chrome forum.  Guess it's their problem.

---

### Post by mörgæs on 2013-02-23
> **r.stiltskin said:**
> I posted this issue on google chrome forum.  Guess it's their problem.

Yes, indeed. Even if a web site is serving really ugly code it should not crash a browser. Please report the bug for the developers to fix.

---

### Post by r.stiltskin on 2013-02-24
It's reported.  Hope they fix it sometime soon.

I notice that this problem only involves the 32 bit versions of chrome/chromium.  This hasn't happened on either of my 64 bit machines.

---

### Post by vasa1 on 2013-02-24
I can access this forum with (stable, not beta) Chrome 25.0.1364.97 (Official Build 183676) 32-bit. Can you try with a new user profile (chrome://settings)?

---

### Post by r.stiltskin on 2013-02-24
Yes.  I've been experimenting with it, and I'm writing this post in chrome right now.  In fact I have deleted the entire ~/.config/google-chrome directory several times in order to start with a completely clean default profile.  (Incidentally, this version 25.0.1364.97 is now listed as BOTH stable and beta.)

So what I've discovered is that the crashing occurs only if I allow chrome to save my password for the forum.  This happens on each of vbulletin forums that I've tried (for which I have a password).  It is also happening on a couple of others (linuxquestions.org, dreamincode.net) which don't seem to be using vbulletin, or at least they don't identify themselves as such.

And for each of the forums that caused chrome to crash, if I delete that forum from the saved-passwords list, I can again log into to it, navigate around the forum, and log out without crashing.

---

### Post by deadflowr on 2013-02-24
> **r.stiltskin said:**
> Yes.  I've been experimenting with it, and I'm writing this post in chrome right now.  In fact I have deleted the entire ~/.config/google-chrome directory several times in order to start with a completely clean default profile.  (Incidentally, this version 25.0.1364.97 is now listed as BOTH stable and beta.)

So what I've discovered is that the crashing occurs only if I allow chrome to save my password for the forum.  This happens on each of vbulletin forums that I've tried (for which I have a password).  It is also happening on a couple of others (linuxquestions.org, dreamincode.net) which don't seem to be using vbulletin, or at least they don't identify themselves as such.

And for each of the forums that caused chrome to crash, if I delete that forum from the saved-passwords list, I can again log into to it, navigate around the forum, and log out without crashing.

What happens if you do this and click on the remember me button next to the login box?

---

### Post by r.stiltskin on 2013-02-24
If I click remember me and save the password it doesn't crash immediately, but after moving from page to page a few times it crashes.

If I don't save the password, it doesn't seem to make any difference whether I check remember me or not.  Either way, I seem to be able to move around the forum freely without crashing.

I've never figured out what "remember me" is actually supposed to do.  Can you shed any light on that?

---

### Post by newjorkcity on 2013-02-24
Ive always found chrome as non-stable maybe this is completely wrong but you should use fire fox because its my favorite browser plus its your default so that kind of in a way makes it more stable and easier to handle:D!

---

### Post by r.stiltskin on 2013-02-24
> **newjorkcity said:**
> Ive always found chrome as non-stable maybe this is completely wrong but you should use fire fox because its my favorite browser plus its your default so that kind of in a way makes it more stable and easier to handle:D!

That's really not helpful.  Let's not turn this into a debate about who likes which browser better.

This is a discussion about a specific problem with chrome that might hopefully help to solve it.

---

### Post by deadflowr on 2013-02-24
> I've never figured out what "remember me" is actually supposed to do. Can you shed any light on that?

The remember me option lets you set it so you will always be logged into the forums when you enter the forums.
So even if you shutdown or reboot, when you re-enter the forums you will automatically be logged in.
This of course will disappear if you delete your profile.

And agreed with the other post that this isn't about browser vs browser, as this is about a particular problem AFAIK causing frustrations for only one user.

If you try launching chrome through the terminal, do you get any errors or anything? (google-chrome is the command). Of course I think you mentioned this before.

I think I saw in an earlier post that you are using the nouveau driver, which IMO is one of the more buggier drivers.

---

### Post by vasa1 on 2013-02-24
What sort of cookie settings do you have?

And if you're using beta, I'm not sure that *google-chrome* is the terminal command. Can you confirm what is used for running the beta from the terminal?

And re. *(Incidentally, this version 25.0.1364.97 is now listed as BOTH stable and beta.)* ... That happens quite frequently when the stable has just been released (not the point releases).

---

### Post by oldos2er on 2013-02-24
> **r.stiltskin said:**
> I've been using google-chrome beta (v 25.0.1364.97 to be exact) for a few days without any problems until today when I used it to log into this forum.  As soon as I finish logging in and it begins to redirect away from the login page, all Chrome windows immediately crash.  None of that silly "snap" nonsense or any other indication of error.  Just gone.


Odd. I'm using the exact same version of Chrome (on Kubuntu 12.10), and haven't had this problem. 

A very long shot, but have your partitions been fsck'ed lately? Any similar problem with other applications?

---

### Post by deadflowr on 2013-02-24
> **vasa1 said:**
> What sort of cookie settings do you have?

And if you're using beta, I'm not sure that *google-chrome* is the terminal command. Can you confirm what is used for running the beta from the terminal?

And re. *(Incidentally, this version 25.0.1364.97 is now listed as BOTH stable and beta.)* ... That happens quite frequently when the stable has just been released (not the point releases).

You can always look in the google chrome.desktop file to see what the exec command is.
Normally you can find it by launching gedit and opening the google chrome in the /usr/share/applications folder.

Also, as with others, I too am running same chrome version (stable) with no problems.

Edit: I forgot the OP is on xubuntu, so I don't remember what the text editor is, but you can use whatever it is in place of gedit.

---

### Post by r.stiltskin on 2013-02-24
> **deadflowr said:**
> The remember me option lets you set it so you will always be logged into the forums when you enter the forums.
So even if you shutdown or reboot, when you re-enter the forums you will automatically be logged in.
So I guess that just does an "end run" around the problem by saving the password in a cookie?  It doesn't really affect whatever's going on with chrome's saved-passwords module.

> I think I saw in an earlier post that you are using the nouveau driver, which IMO is one of the more buggier drivers.
Well, I've been using nouveau for many months without any problems, and recently when I tried nvidia-current there were some issues (which may or may not have been related to nvidia-current) although I don't remember the details, so I uninstalled it and went back to nouveau.  I don't think its the culprit here.

> If you try launching chrome through the terminal, do you get any errors or anything?
Brilliant idea!  I hadn't thought of trying that.

But I'm not getting any bright ideas from the terminal output.  The one directly related to password-saving is the gtk warning about a ridiculous widget size.  Here's the whole story:

This is output immediately after opening chrome with no profile. In other words, first I deleted the .config/google-chrome folder, then opened chrome:
```
$ google-chrome
[2689:2689:0224/143833:ERROR:master_preferences.cc(110)] Failed to read master_preferences file at /opt/google/chrome/master_preferences. Falling back to default preferences.
[2689:2713:0224/143834:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2689:2713:0224/143834:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2689:2689:0224/143834:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[2689:2689:0224/143845:ERROR:extension_prefs.cc(1540)] Bad or missing pref 'version' for extension 'aohghmighlieiainnegkcijnfilokake'
[2689:2689:0224/143845:ERROR:extension_prefs.cc(1540)] Bad or missing pref 'version' for extension 'apdfllckaahabafndbhieahigkjlhalf'
[2689:2689:0224/143845:ERROR:extension_prefs.cc(1540)] Bad or missing pref 'version' for extension 'coobgpohoikkiipiblmjeljniedjpjpf'
[2689:2689:0224/143846:ERROR:extension_prefs.cc(1540)] Bad or missing pref 'version' for extension 'blpcfgokakmgnkcojhhkbfbldkacnbeo'
[2689:2689:0224/143846:ERROR:extension_prefs.cc(1540)] Bad or missing pref 'version' for extension 'pjkljhegncpnkpknbcohdijeoejaedia'
[2689:2689:0224/143855:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
[2689:2689:0224/143901:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()


```The last two lines were generated when I clicked in the chrome window.

Then I closed chrome (which has now created a default google-chrome directory) and opened it again (and told it to stop asking to be default browser):
```

$ google-chrome
[2822:2845:0224/144118:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2822:2845:0224/144118:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[2822:2822:0224/144119:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[2822:2822:0224/144119:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()

```
That last line about omnibox_view_gtk was repeated when I clicked on the chrome window.

There was no terminal output when I opened ubuntuforums.org.  Then I logged into the forum and when I clicked to have chrome save the password the output was
```
(google-chrome:2822): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -2147483648 and height -2147483648

```
Then I moved around the forum moving from page to page a few times (~5) and then logged out.  As soon as I logged out chrome crashed with:
```

le/chrome/chrome: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted (core dumped)

```
Thereafter, each time I restart chrome and try to open ubuntuforums.org, the output is:
```

$ google-chrome
[3025:3048:0224/145134:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3025:3048:0224/145134:ERROR:object_proxy.cc(624)] Failed to get name owner. Got org.freedesktop.DBus.Error.NameHasNoOwner: Could not get owner of name 'org.chromium.Mtpd': no such name
[3025:3025:0224/145135:ERROR:object_proxy.cc(529)] Failed to call method: org.chromium.Mtpd.EnumerateStorages: object_path= /org/chromium/Mtpd: org.freedesktop.DBus.Error.ServiceUnknown: The name org.chromium.Mtpd was not provided by any .service files
[3025:3025:0224/145135:ERROR:omnibox_view_gtk.cc(431)] Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
le/chrome/chrome: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted (core dumped)

```
I can "fix" it by opening chrome and deleting the saved password & then I can log in, not save the password, move around the forum, log out, etc.,  and chrome doesn't crash.

---

### Post by r.stiltskin on 2013-02-24
> **vasa1 said:**
> What sort of cookie settings do you have?

All default settings:
allow local data to be set
show all images
allow javascript
allow sites to become default handlers
run plug-ins automatically (although none are installed)
don't allow pop-ups
ask me when site tries to track my location
ask me when site wants to show desktop notifications
ask me when site tries to disable mouse cursor
ask me when site wants to use a plug-in


> 
And if you're using beta, I'm not sure that *google-chrome* is the terminal command. Can you confirm what is used for running the beta from the terminal?
It is google-chrome, but as I said, this version is now also listed as "stable".  If they were actually two different versions it would make sense for the beta to be started with a different command -- but I can't say for certain.

---

### Post by r.stiltskin on 2013-02-24
> **oldos2er said:**
> Odd. I'm using the exact same version of Chrome (on Kubuntu 12.10), and haven't had this problem. 
Possibly because in Kubuntu you're using kwallet to save the passwords?

Also possibly because you're running 12.10 and I'm running 12.04.

Also possibly because mine started out as Kubuntu, and then I tried gnome, and then I recently dumped most of kde4 and gnome and installed xubuntu-desktop and xfce-goodies.  I believe that I kept the necessary gnome stuff but maybe I screwed something up (although so far everything else, including firefox password-saving) has been working.

...

> A very long shot, but have your partitions been fsck'ed lately? Any similar problem with other applications?Disks have been checked.  And no other problems that I'm aware of.

---

### Post by oldos2er on 2013-02-24
> **r.stiltskin said:**
> Possibly because in Kubuntu you're using kwallet to save the passwords?

I do use KWallet, but not with Chrome.

---

### Post by r.stiltskin on 2013-02-24
> **oldos2er said:**
> I do use KWallet, but not with Chrome.

Ah, well, it remains a mystery.

When I google my cairo-surface error it brings up lots of hits -- bug reports in various places, not all directly related to password-saving, and many not related to chrome at all.  So I guess it's not the passwords per se, but just that that function is triggering an error someplace else.

I probably have some inconsistency resulting from changing desktops, but I'm not in a position to reinstall the whole distro now so I'll just have to live with it.

---

### Post by Kilz on 2013-05-05
I havent posted to the forums in awhile. I no longer use Ubuntu for reasons related to how members were treated during the change to Unity. But I cant leave people with a problem and not have the fix when I know it. I anticipate that more people will be posting on this topic soon.

I still have a few instlations that I take care of for my church. One of them, running xubuntu, had Chrome crashing and giving the same error as in [post 20]("http://ubuntuforums.org/showthread.php?t=2119386&p=12528165#post12528165")

```
Not implemented reached in virtual void OmniboxViewGtk::ApplyCaretVisibility()
le/chrome/chrome: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
Aborted
```

The problem after a search was related to how the passwords were stored in the keyring. Adding 

--password-store=basic 

To the launcher command stoped the crashing as it stores the passwords in a file and not the keyring. Obviously this isnt a safe way to store them if you are concerned about password security. But at least it lets you use Chrome.

---

### Post by r.stiltskin on 2013-05-05
I guess I share your feelings about Unity.  I've been happily using Xubuntu for the past 6 months or so.

As to this thread, it feels like ancient history.  My "solution", if I may call it that, was to decide that I had no compelling reason to continue providing Google with free product testing services.  So I stopped wasting time with Chrome and returned to Firefox.

---


---
title: "Chrome gets overlaid on desktop..."
date: 2013-12-11
forum: Desktop Environments
---

### Post by ahow628 on 2013-12-11
First of all, apologies for the terrible thread title. If anyone has a better suggested title after hearing the issue, I'd be happy to hear it.

I'm running 12.04.3 on a Toshiba Portege z935.

After I run Chrome for a while, if I close it, I have an image of a former state of Chrome (not necessarily as it was when closed) stuck on my desktop. Additionally, you can see the Chrome icon has some little gray arrows around it. If I reopen Chrome, the gray arrows turn white and if I close Chrome again, they go back to gray and the desktop still looks like the screenshot below.

[ATTACH=CONFIG]248535[/ATTACH]

When I first boot up, the desktop is the normal Unity Gnome desktop that comes installed with stock 12.04.3. The Chrome that gets overlaid doesn't happen right away. I can't figure out what is causing it but it isn't related to time, I don't believe.

Any help would be appreciated. Thanks!

---

### Post by Copper Bezel on 2013-12-12
When you right-click the desktop, do you get the normal Nautilus menu - New Folder, New Document, Paste, etc.?

---

### Post by ahow628 on 2013-12-12
No. Right clicking yields nothing. Also, nothing showing from the Chrome window is clickable (hyperlinks or the "Cancel" button).

EDIT: Possible breakthrough! I was looking at the screenshot I posted and remembered that was about when I closed the lid of the laptop (it doesn't suspend, it just turns off the screen). So on a hunch, I rebooted, opened Chrome, closed the lid and reopened, and - VOILA! - Chrome was overlaid like that again.

Still doesn't explain why it's happening. Any suggestions on logs or something I can post to help with diagnosis?

---

### Post by Copper Bezel on 2013-12-12
Nope, that's what my question was already. Nautilus isn't running, and nothing is rendering the background, so you're looking at artifacts on the root window.

You have desktop icons turned off in Gnome Tweak Tool, right? Turn them back on again and let me know what happens.

---

### Post by ahow628 on 2013-12-12
Ok, I didn't understand why you were asking the question, but now it makes sense. Nautilus is getting killed when I shut the lid of the laptop, I guess. Can I reinstall it? Maybe I'll give it a go and report back.

EDIT: Nope, ```
sudo apt-get install --reinstall nautilus
``` didn't fix it.

---

### Post by Copper Bezel on 2013-12-13
I think it's not that Nautilus gets killed when you close the lid, but that the graphics card gets flushed, which is why you no longer *see *the desktop background. Until that happens, the desktop is still rendered onto the root window whether or not Nautilus is actually still running. 

Does simply *running* Nautilus bring your backdrop back after it's gone? Try launching it from a terminal, and, yeah, post the results.

---

### Post by ahow628 on 2013-12-13
That worked. Opened a terminal and typed 'nautilus' and the files on my desktop and the desktop itself reappeared and the ghosting went away. Once I Ctrl+C nautilus and exit terminal, the desktop background still shows but the files on the desktop are no longer visible.

---

### Post by Copper Bezel on 2013-12-13
Yep. So something is killing Nautilus, and it doesn't respawn automatically like it used to in Gnome 2.x-based Unity. Now we just need to figure out what's killing it in the first place. 

Leave it running from the terminal for a while. Open and close the lid, go through your normal tasks, and periodically check the terminal. We'll see if, the next time it crashes, we get an exit message.

---

### Post by ahow628 on 2013-12-14
Ok, the first thing is that when I used to log in, my files were on the desktop. Now, i boot to an empty desktop.

So I open a terminal and type 'nautilus'. The desktop items suddenly appear, along with a Thunar window and terminal says:
```
andy@portege:~$ nautilusInitializing nautilus-dropbox 1.6.0
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

I think all of that is relatively normal. I don't see any obvious errors (I don't use Samba).

Now that I have Nautilus running, I opened a Chrome window, close the lid and open it again (I don't have suspend enabled - it just turns the screen off aka "Do Nothing" in the Power Options).

This time it doesn't show the ghosting. 

If I Ctrl+C Nautilus and type 'exit' in the terminal (thus closing it out), then the terminal window is stuck on the desktop and none of the files on the desktop are clickable.

So I guess it sounds like the Nautilus daemon is maybe no longer starting automatically.

---

### Post by Copper Bezel on 2013-12-14
Sounds exactly right. If "Have file manager handle the desktop" is checked in Gnome Tweak Tool / Ubuntu Tweak / wherever you set your advanced settings - the dconf key, if you want to check it directly, is org.gnome.desktop.background show-desktop-icons - just add Nautilus to Startup Applications. 

Sounds like Solved! Go ahead and mark the thread if you're done, or we can try to track down why Nautilus isn't getting run if you'd like.

Edit: Sorry, the command to put in Startup Applications is nautilus --no-default-window , which is the corresponding command to nautilus --no-desktop and launches *only *the desktop, but no FM windows.

---


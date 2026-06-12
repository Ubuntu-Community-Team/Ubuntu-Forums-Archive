---
title: "Ensure Xfce retains &quot;manage desktop&quot; setting across logins"
date: 2007-10-05
forum: Desktop Environments
---

### Post by thhp on 2007-10-05
Hi,

I'm running Ubuntu 7.04 with XFCE4. I'm having trouble getting XFCE to retain my desktop settings over logins.

Here are some details:

I installed XFCE via "apt-get install xubuntu-desktop" for a lighter desktop. On my first login, I checked the tickbox "Allow XFCE to manage desktop" (Settings->Desktop Settings). I have configured xfce4-session to save my session on logout by checking the tickbox "Automatically save session on logout" (Settings->Sessions and Startup).

The problem is that every time I log in, the "Allow XFCE to manage desktop" setting is lost, and my desktop is hidden behind the old wallpaper I used in Gnome. Checking the running processes via "ps -ef" showed that nautilus was running. If I re-set the "Allow XFCE to manage desktop" checkbox, nautilus is killed -- so I think the problem is basically that nautilus is getting run when it shouldn't.

Can anyone help me to solve this? I believe I need to either

 * Stop nautilus running at all at login (ideal)
 * Add the "--no-desktop" option to nautilus' default arguments to prevent it clobbering my desktop

Thanks in advance for any suggestions!


Tom

---

### Post by thhp on 2007-10-09
Interestingly, my Xubuntu startup problems have got worse! 

I now have both the calendar (orage) and the XFCE help/info dialog starting at boot, which is really annoying.

If anyone can help me solve these problems I'd be grateful!

T

---

### Post by thhp on 2007-10-09
I managed to solve my problem with some help from the #xfce irc channel.

It seems xfce4-session caches information about your running session in ~/.cache/sessions. This file is read on startup, and written to when you save your session (typically on logout, either via explicitly telling XFCE to do so, or if you've set it to automatically save your session).

My problem was that somehow nautilus had got into that cached session file, and somehow saving the nautilus-free session on logout didn't fix the cache.

The solution:

1. Log out of XFCE.
2. Use CTRL+ALT+F1 to get a console, and log in from there.
3. Remove the xfce4-session cache file from ~/.cache/sessions (you could probably edit it, if you want to keep your other session-based configuration).
4. Log out, and return to X using CTRL+ALT+F7
5. Log in to an XFCE session again.

I'm now running nautilus-free :)


Hope this helps someone!

---

### Post by wrathkeg on 2007-10-18
> **thhp said:**
> 
Hope this helps someone!

Just worked for me: thanks!
WK

---

### Post by Dwood108 on 2007-10-20
I had the same problem and the following worked for me:



   1. In the XFCE session manager (Settings > XFCE4 Session and Startup Settings), check the box that says "Show session selection at startup."
   2. Log out and log back in.
   3. Click 'New Session' when the session selector appears, and name it whatever you want.
   4. The next time you log in, select the session you created in the previous step. XFCE should be managing the desktop right at startup, with no need to re-check the "Allow XFCE to manage desktop" box.

once this works you can turn off the session selector at startup and go directly to your new session on future logins.

---


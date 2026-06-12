---
title: "Remove/Hide IM Status Icons from Messaging Menu"
date: 2012-06-22
forum: Desktop Environments
---

### Post by gmartinr on 2012-06-22
I removed empathy and gwibber, but cannot find a way to remove or hide the IM Status Icons from messaging menu.

Is the only option is just removin the indicator-message package?

I use Ubuntu 12.04 (precise)

---

### Post by gordintoronto on 2012-06-22
Sometimes, we just have to live with these tiny distractions.

---

### Post by gmartinr on 2012-06-25
:lolflag: I refuse to live with that. Well, the i've removed the indicator-messages package.

---

### Post by markbl on 2012-06-25
> **gmartinr said:**
> :lolflag: I refuse to live with that. Well, the i've removed the indicator-messages package.
No need for that. Read about blacklisting at [https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu).

---

### Post by gmartinr on 2012-06-25
> **markbl said:**
> No need for that. Read about blacklisting at [https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu).

That's for hide emphaty, emesene, thunderbird or everything else, but the IM Status. Or i'll need say sorry because i can't figure how to do that.

---

### Post by UnaXdk on 2012-07-08
Hey gmartinr

Did you ever find out how to remove the IM-status icons? I have uninstalled everything I could think of which would remove them, but to no avail.

I only want my messaging indicator to have the gmail notifier and not all the other things. So far it's only the IM-status icons I got left.

---

### Post by oddowl on 2012-09-18
I'm pursuing the same cause, but I went the other route - I totally  removed indicator_messages, as I expected that after this my gm_notify  icon will appear on panel, but no luck :( 

I tried other Gmail  notifiers, but none of them appear in panel. It seems that Unity is  forcing every messaging app to integrate into messaging menu, and if  it's removed, then there seems to be no way to add Gmail (or any other  standalone messaging app-indicator) on panel. I hope I'm wrong, but I  haven't figured a way yet...

---

### Post by markbl on 2012-09-18
> **oddowl said:**
> 
I tried other Gmail  notifiers, but none of them appear in panel.

I could not find a gmail notifier which integrates into both Unity and Gnome Shell so I created my own [gmail-indicator](https://github.com/bulletmark/gmail-indicator).

---


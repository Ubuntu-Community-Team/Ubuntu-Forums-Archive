---
title: "Nautilus window &quot;goes dark&quot;"
date: 2011-06-04
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-06-04
I'm still running Ubuntu 10.04 LTS -- its been a while -- and I've been
persistent about applying updates.  Recently, I've started seeing a problem with Nautilus -- the Gnome file manager.

I will open a Nautilus window and:
[list]
[*]it does not open
[*]it opens but does not respond
[*]when I try to do something, the window darkens
[*]when I try to close the window, I'm told "Not Responding"
[/list]

Can anyone suggest what might be going on here?
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-06-04
[highlight]... follow-up details ...[/highlight]

I renamed the folder $HOME/.nautilus to something else and started
nautilus again.  I used both the gnome panel and the command line
to accomplish the launch.

**Same Error result**

Yes, I got a fresh copy of $HOME/.nautilus but I also got the darkend
window.

The failing workstation does not have a second "desktop" user login defined at this time.

While I had trouble with "Switch User" nautilus works fine when I
login root on a second desktop. [i]Therefore it is not a problem with
nautilus itself, but rather the world of the user where it fails.[/i]


Thanks,
~~~ 0;-Dan

---

### Post by arpad9 on 2011-06-04
Sounds like something might be blocking on I/O?  Do you have something in your Places that isn't responding?  External smb share or optical drive or something?

---

### Post by steinerd on 2011-06-04
I agree, able to recreate with a downed SMB share that has been hardlinked into nautilus.  Would this situation not clear up if the .nautilus directory was recreated for the user?  possibly something not mapping in the /media directory?

My [UBUNTU blog.....]("http://deep-sea.realservers.info/ubuntu/")

---

### Post by Shadow Warrior on 2011-06-04
[SIZE=3]I believe that this is the identical problem described in this thread. My computer can run several hours without a problem, then the screen suddenly goes dark and becomes unresponsive. A string of messages revered to the LAMP I had installed; but after removing that, the problem persists. Is there a command that can salvage this situation?[/SIZE]

---

### Post by SaintDanBert on 2011-06-07
> **steinerd said:**
> 
...Would this situation not clear up if the .nautilus directory was recreated for the user?  possibly something not mapping in the /media directory?
...

I tried that without any success.
Yes, I got a fresh nautilus profile.
Yes, still got the grey-ed out window.

Still stumpled,
~~~ 0;-/

---

### Post by SaintDanBert on 2011-06-07
> **Shadow Warrior said:**
> [SIZE=3]I believe that this is the identical problem 
...
then the screen suddenly goes dark and becomes unresponsive
...

In your case, **the screen** goes dark. This says (to me) that the entire desktop is stalled waiting on something.

In the case described with this thread, only **one window** goes dark but the rest of the desktop stays alive. (In truth, all nautilus windows go dark if there are several open.)

Still stumpled,
~~~ 0;-/

---

### Post by SaintDanBert on 2011-06-07
> **steinerd said:**
> I agree, able to recreate with a downed SMB share that has been hardlinked into nautilus.
...


Don't have any SMB shares.
I do have mountpoints for several partitions -- some of which are NTFS -- that are all on the same drive.
I do have mounted external USB connected drives -- some of which may be NTFS -- but the mix of drives changes all the time.

Still stumpled,
~~~ 0;-/

---


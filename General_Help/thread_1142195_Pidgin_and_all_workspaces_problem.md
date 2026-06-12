---
title: "Pidgin and all workspaces problem"
date: 2009-04-28
forum: General Help
---

### Post by jacksonpollack on 2009-04-28
I recently upgraded from Intrepid to Jaunty, but am experiencing a problem with Pidgin: the buddy list appears in the panel on all workspaces, not just in the workspaces where the window actually is. It is selected to be "only in this workspace", so it shouldn't do that – and indeed didn't back when I used Intrepid (and Hardy before that). I uninstalled the program completely, and reinstalled it, but the problem is still there.
Is there anything I can do to fix this?

Thanks ahead of time...

---

### Post by khc on 2009-04-29
This is caused by a faulty patch that ubuntu introduced, there's a bug filed in launchpad but I don't recall the number

---

### Post by jacksonpollack on 2009-04-29
Hmm. I'll take it that there's nothing I can do then?
I've tried searching Launchpad for the bug, but I can't seem to find anything similar to my problem. If anybody can find it, I'd love to read up on it. 

I can, at least, temporarily fix the problem. If I have another program open and showing in the panel, I can move the Pidgin Buddy List button, and it magically disappears on that workspace and all others where the Buddy list window isn't actually open on. I guess I'll just have to do this every time I start up the program...

I'm starting to notice some other weird workspace issues too though. Occasionally, when I first start Firefox, it appears in two (but not all) of my workspaces as separate instances. I can just close one, but again, it's a new problem. 

Does anyone else have these or similar problems in Jaunty?

---

### Post by jacksonpollack on 2009-05-01
Am I really the only one experiencing this problem?

But now I have worse problems anyhow, namely my title bars on all my programs' windows disappearing every time I reboot...

---

### Post by FAiN182 on 2009-05-10
I have the same problem... pidgin shows in all the workspaces..

---

### Post by khc on 2009-05-12
> **jacksonpollack said:**
> Hmm. I'll take it that there's nothing I can do then?
I've tried searching Launchpad for the bug, but I can't seem to find anything similar to my problem. If anybody can find it, I'd love to read up on it. 

The bug is [https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/341142](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/341142)

---

### Post by motang on 2009-05-24
I have that problem also, and it's freaking annoying!

---

### Post by adyroman on 2009-06-15
Me too... Have you guys found any workaround?

---

### Post by H2SO_four on 2009-06-15
> **FAiN182 said:**
> I have the same problem... pidgin shows in all the workspaces..

me too, but thankfully it doesn't bug me that much.

---

### Post by mcduck on 2009-06-15
> **adyroman said:**
> Me too... Have you guys found any workaround?

Not really, but I use Compiz to hide the Buddy List completely from the Window List. At least it won't appear on wrong desktops any more, and with the Notification Area-icon enabled it's still easy enough to access..

To do that jus open Compizconfig Settings Manager, browse to Window Rules-plugin, and on the Matches-tab add "title=Buddy List" to "Skip Taskbar".

I also decided to add it to "Non minimizable windows" to get rid of the now pointless minimize-button, and "Non maximizabe windows" just because I won't need that one either and it looks better this way. ;)

---

### Post by khc on 2009-06-16
> **adyroman said:**
> Me too... Have you guys found any workaround?

If you find it annoying, complain at the aforementioned bug report so they will take out the patch.

---

### Post by jacksonpollack on 2009-07-08
Hm, I think this bug report is more along the lines of what we're talking about:
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/346840](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/346840)

Someone there mentioned upgrading Pidgin to 2.5.6 solves the problem, though I haven't had time to try that out yet.

What you can do (and this is kinda ghetto but it works) is move the buddy list button on the menu bar to the left or right of another program's button. This seems to do nothing, but if you then switch to another workspace, you'll notice that the buddy list button isn't there and will only be showing on the proper workspace (as it should). If you move the button when you are not on the workspace where the actual buddy list is located, the button will disappear before your eyes!
This needs to be done each time Pidgin is started.

---

### Post by mastapat11 on 2009-09-13
> **jacksonpollack said:**
> Hm, I think this bug report is more along the lines of what we're talking about:
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/346840](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/346840)

Someone there mentioned upgrading Pidgin to 2.5.6 solves the problem, though I haven't had time to try that out yet.

What you can do (and this is kinda ghetto but it works) is move the buddy list button on the menu bar to the left or right of another program's button. This seems to do nothing, but if you then switch to another workspace, you'll notice that the buddy list button isn't there and will only be showing on the proper workspace (as it should). If you move the button when you are not on the workspace where the actual buddy list is located, the button will disappear before your eyes!
This needs to be done each time Pidgin is started.


This solution worked for me. thanks!

---


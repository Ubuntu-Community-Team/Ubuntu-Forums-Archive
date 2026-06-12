---
title: "Gnome Extensions complains about my native host connector not supporting v6 API"
date: 2022-07-13
forum: Desktop Environments
---

### Post by Paddy Landau on 2022-07-13
On Ubuntu 20.04, when I go to [Gnome Shell Extensions]("https://extensions.gnome.org/") in my browser, I have a new error message:
> Your native host connector do not support following APIs: v6. You should probably upgrade native host connector or install plugins for missing APIs. Refer to [the documentation]("https://wiki.gnome.org/Projects/GnomeShellIntegrationForChrome/Installation") for instructions.
[The instructions]("https://wiki.gnome.org/action/show/Projects/GnomeShellIntegration/Installation#Ubuntu_Linux") tell me to install chrome-gnome-shell from the standard repositories. But it was already installed on Ubuntu 20.04 nearly two years ago, and on 22.04 a couple of months ago.

[LIST]
[*]Ubuntu 20.04 and 22.04 both show this message.
[/LIST]
I note that the version of chrome-gnome-shell is the same on both machines (version 10.1-5).

I'm using Chrome, in case that makes a difference, though I see the same error on Firefox.

So far, everything seems to work OK.

[LIST]
[*]What does the message mean?
[*]Should I do something about it?
[/LIST]
Thank you

EDIT: 22.04 also shows this message, now.

---

### Post by #&amp;thj^% on 2022-07-13
> **Paddy Landau said:**
> 

[LIST]
[*]What does the message mean?
[*]Should I do something about it?
[/LIST]
Thank you
I remember you like snaps, if this is the case still, a browser installed as a snap cannot connect to the main system, also with the connector "chrome-gnome-shell", which establishes the communication between the Gnome Shell Extensions website and Gnome Shell.
BTW: If you have Flatpak enabled, you can install [Extension Manager,]("https://flathub.org/apps/details/com.mattjakeman.ExtensionManager") a GTK4 desktop application that allows to browse and install extensions without having to use a browser.

---

### Post by Paddy Landau on 2022-07-13
> **1fallen said:**
> … you can install [Extension Manager]("https://flathub.org/apps/details/com.mattjakeman.ExtensionManager")
I just installed it. It's quite nice, thank you.
> **1fallen said:**
> I remember you like snaps…
I have come to prefer flatpak now :)

But the browser is Chrome, which is installed as a standard deb (it's not available as snap or flatpak). And, on Ubuntu 20.04, Firefox is also a deb.

So, it doesn't answer the question, sorry.

---

### Post by naknak987 on 2022-07-15
I just want to say that I'm having the same issue with 22.04. If I find a solution I'll post it here.

---

### Post by codiecher on 2022-07-17
Having the same issue over here on Ubuntu 20.04, can't install any extensions from microsoft edge, firefox.

---

### Post by Paddy Landau on 2022-07-17
> **naknak987 said:**
> I just want to say that I'm having the same issue with 22.04. If I find a solution I'll post it here.
It's just started to happen on my 22.04 as well!

I think that it's time to report this as a bug.
> **codiecher said:**
> Having the same issue over here on Ubuntu 20.04, can't install any extensions from microsoft edge, firefox.
I don't have this problem on 20.04 or 22.04, using Chrome or Firefox (I haven't tried Edge).

For this, you might want to create a new thread. When you do so, please post the link here, so that we can also follow it in case it's related.

---

### Post by vanadium on 2022-07-17
Bug report is available here: [https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/5622](https://gitlab.gnome.org/GNOME/gnome-shell/-/issues/5622), and likely will be fixed soon on the side of the website. Only users of the latest Gnome Shell versions (42.3.x releases) cannot install extensions because of this. For Ubuntu users, extensions can still be installed despite the message.

---

### Post by Paddy Landau on 2022-07-17
> **vanadium said:**
> Bug report is available here…
Thank you.

So, that is definitely unrelated to the problem that this thread is talking about (API v6).

---

### Post by #&amp;thj^% on 2022-07-17
Please see this: [https://gitlab.gnome.org/Infrastructure/extensions-web/-/issues/194](https://gitlab.gnome.org/Infrastructure/extensions-web/-/issues/194)

---

### Post by Paddy Landau on 2022-07-17
> **1fallen said:**
> Please see this: [https://gitlab.gnome.org/Infrastructure/extensions-web/-/issues/194](https://gitlab.gnome.org/Infrastructure/extensions-web/-/issues/194)
Thank you. That's Gnome version 42.3.1, which affects neither Ubuntu 20.04 nor 22.04.

---

### Post by #&amp;thj^% on 2022-07-17
It seems  to affect you and others dose it not?
Your getting a bit picky IIMHO, that info was mostly gleamed from Arch so versions are different.
I hear a fix is being pushed out today or tomorrow if all goes well.
Note to self, expect resistance from Paddy. ;)
BTW: I show:
```
gnome-shell --version
GNOME Shell 42.2

```

---

### Post by Paddy Landau on 2022-07-17
> **1fallen said:**
> Your getting a bit picky IIMHO…
You're being a bit sarcastic, which is uncalled for.

I'm not getting the fault where I can't install. As you yourself show, the Gnome version on Ubuntu 22.04 is 42.2. And, I can install extensions just fine.

In any case, this thread is about a different error, which you can see in the title and in my OP.

---

### Post by #&amp;thj^% on 2022-07-17
> **Paddy Landau said:**
> You're being a bit sarcastic, which is uncalled for.


Sarcastic is a matter of the view I guess, lighten-up a bit. :popcorn: But apologies for any hurt feelings you may have encountered.
> **Paddy Landau said:**
> 
I'm not getting the fault where I can't install. As you yourself show, the Gnome version on Ubuntu 22.04 is 42.2. And, I can install extensions just fine.

Yep that was clear enough, and to add I see the same as you. And I can also install extensions none the less.(Screenshot to confirm)
Perhaps it's best if we just "avoid" each other here in forums...;)

---

### Post by franklinyu on 2022-08-03
Not only the version is different. The symptom is different as well.

The problem described there mentions users unable to install extension. If I understand your case correctly, extensions can be installed without issue, despite that warning message. We may as well file a new issue to GNOME.

---

### Post by Paddy Landau on 2022-08-03
> **franklinyu said:**
> Not only the version is different. The symptom is different as well.

The problem described there mentions users unable to install extension. If I understand your case correctly, extensions can be installed without issue, despite that warning message. We may as well file a new issue to GNOME.
Yes, that's all correct. I have filed a [new issue]("https://gitlab.gnome.org/Infrastructure/extensions-web/-/issues/196"). Please upvote it to support it.

---


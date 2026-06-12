---
title: "Epiphany sidebar is blank . . . ?"
date: 2005-05-16
forum: Desktop Environments
---

### Post by GTKpower on 2005-05-16
I'm really liking Epiphany, even though I'm a die-hard Firefox user.

In Firefox, I had all my bookmarks displayed in a sidebar.  Very useful.

I installed all the Epiphany extensions, and it too, gives me a sidebar.  But it's blank.  I'd like all my bookmarks to be accesibly from that sidebar.  Yes, there is a separate bookmark box, but that's in a separate window that I have to activate and position every time I start Epiphany.

Right now, I hve the Epiphany sidebar enabled, and it says "No sidebars installed", and it seems I can't do anything with it.

Any help?  How can I make my bookmarks show in that sidebar?

Thanks.

---

### Post by ow50 on 2005-05-16
This is something I have wondered as well. The text "No sidebars installed" is quite annoying without info on how to install sidebars.

For bookmarks I've been the bookmarks bar. Now that I've gotten used to it, I find it more convinent than the sidebar. However, for occasional history browsing the sidebar would be useful.

---

### Post by GTKpower on 2005-05-17
Guess no one knows . . . .

---

### Post by andrewski on 2006-05-31
Well, at this point in Dapper there is documentation in this under Help | Extensions.  Also, there was a shotgun bug that I filed just for this purpose: [https://launchpad.net/distros/ubuntu/+source/epiphany-extensions/+bug/38683]("https://launchpad.net/distros/ubuntu/+source/epiphany-extensions/+bug/38683").  It's too late at this point (I've had no time!), but maybe we could get this in for dapper-updates? O:)

---

### Post by juknevij on 2007-11-19
I just added the google talk gadget to the so far useless
sidebar in Ephiphany. In [http://google.com/talk](http://google.com/talk)
click on "launch google talk gadget" and inside the gadget
add to bookmarks.

---

### Post by dbbolton on 2008-02-04
Any news on this?

---

### Post by andrewski on 2008-02-04
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/epiphany-extensions/+bug/38683](https://launchpad.net/ubuntu/+source/epiphany-extensions/+bug/38683) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				> **dbbolton said:**
> Any news on this?
As noted on the Launchpad bug, this has been fixed. The documentation describes where to find sidebars.

---

### Post by dbbolton on 2008-02-04
The link on where to find sidebars: 

[http://www.dmoz.org/Netscape/Sidebar/](http://www.dmoz.org/Netscape/Sidebar/)


The contents of that page:

**[SIZE=+1]The page you attempted to access does not exist on this site.[/SIZE] ** **The closest matches are: **
[LIST]
[*]**[Open Directory Main Page]("http://www.dmoz.org/") **[/LIST]

---

### Post by andrewski on 2008-02-04
As Sebastian mentioned on the bug, that's a new issue and should be reported (probably upstream).

---

### Post by dbbolton on 2008-02-04
> **andrewski said:**
> As Sebastian mentioned on the bug, that's a new issue and should be reported (probably upstream).
I saw that, but I'm not really interested in the bug reporting. I would like to know if there has been any recent development with the sidebar; exempli gratia, whether there is another list somewhere.

---

### Post by dbbolton on 2008-05-23
Any news on this?

---

### Post by jdarias on 2008-06-04
I have this hack:
```
javascript:window.sidebar.addPanel('page title','http://www.page address.com','')

```
You have to replace page title and the address for the one you want. then you paste all the code in the location bar and hit enter.
Sadly, it opens the links in the sidebar, not in the adyacent tab. would be great to know how to do this.

---


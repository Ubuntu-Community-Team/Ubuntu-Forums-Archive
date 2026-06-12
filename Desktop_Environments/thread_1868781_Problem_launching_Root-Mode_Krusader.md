---
title: "Problem launching Root-Mode Krusader"
date: 2011-10-24
forum: Desktop Environments
---

### Post by johnherron on 2011-10-24
Hello, folks. :)

Krusader happens to be my favorite file manager (it is, IMHO, quite a bit more nimble and comprehensive than Ubuntu's default, Nautilus).

There is just one flaw: when I need to do things that require me to act as 'root', I would have to run Root-Krusader but can't, because kdesu is not to be found anywhere - neither in apt-get nor on the web. 
When I attempt to start root-mode Krusader, I get this message:
[I]"Can't start root mode krusader, because krusader or kdesu is missing from the path. Please configure the dependencies in Konfigurator!"
[/I]
How can I correct the situation and solve the problem?

Thanks for helping.
jdh

---

### Post by PaulW2U on 2011-10-24
I think you need to install **kdesudo** and set **/usr/bin/kdesudo** against kdesu on the General tab of Dependencies in Konfigurator (Settings).

At least that is what I have running Kubuntu 11.04 and 11.10. Hope that helps.

**Edit:** I'm also thinking that entering the path to gksudo might work as well. :?:

---

### Post by johnherron on 2011-10-27
Setting the path to /usr/bin/kdesudo was accepted by Konfigurator, but attempting to then launch Root-mode Krusader was met with the same error message I reported in my original posting.

Update Manager then suggested installing/updating what appeared to be about forty KDE applications or libraries. I accepted and a subsequent Krusader search for kdesu yielded the following

[http://ubuntuforums.org/attachment.php?attachmentid=205600&stc=1&d=1319729479](http://ubuntuforums.org/attachment.php?attachmentid=205600&stc=1&d=1319729479)

Could you perhaps suggest which of the kdesu files shown I might use as a proper path?

Thanks for helping.
jdh

---

### Post by PaulW2U on 2011-10-27
> **johnherron said:**
> 
Could you perhaps suggest which of the kdesu files shown I might use as a proper path?

Sorry John, I'm out of further ideas at this time. I've given you the path that I use but if that doesn't work ... ](*,)

I've never been one to mix KDE and Gnome any more than I have to. The path that I use has worked on every Kubuntu installation that I have used. I'm probably missing something very obvious. Perhaps someone will come along and tell me what that is.

Are there any Gnome users reading this that have krusader installed that can help?

---

### Post by donmaz on 2012-08-06
G'day People,

I'm having s similar problem as johnherron in that I can't get Krusader to run properly in root mode. While in Krusader in normal mode I can elect to run it in root mode under the tools menu, it asks for and accepts my password but then stays in the original screen. Of course any actions I try to take as root are rejected with the usual "access denied". I would have thought that when it accepts my password another screen should open which would allow root activity. Any advice would be appreciated.

---

### Post by mikia on 2013-02-13
In Ubuntu 12.04 i386 Desktop I use this:
1. Make shortcut for Krusader on desktop.
2. Right click on shortcut and Properties
3. Change field Command. 
Old value: krusader -caption "%c" %i
New value: **gksudo krusader**
4. Close

---

### Post by insink71 on 2013-08-05
> **mikia said:**
> In Ubuntu 12.04 i386 Desktop I use this:
1. Make shortcut for Krusader on desktop.
2. Right click on shortcut and Properties
3. Change field Command. 
Old value: krusader -caption "%c" %i
New value: **gksudo krusader**
4. Close

This runs krusader in root mode all the time.  A better fix in my opinion is:
[LIST]
[*]Download and install kdesudo 
[/LIST]
From within krusader:
[LIST]
[*]Choose Settings -> Configure Krusader 
[*]In the pop-up box choose Dependencies 
[*]Under the General tab [which it defaults to], top line is kdesu.. in the blank space provided type: '/usr/bin/kdesudo' [without apostrophes] 
[*]Might have a couple pop-ups the first time you enable [letting you know what packages are enabled and what are not], #1 rule: "Don't panic!" just hit ok..ok etc. 
[*]Boom! you get the Root access window [when called], next time [you need root explorer] it won't have the previous warning/config messages.. so you are good to go. 
[/LIST]

This is a very simple fix within the GUI system.  Hope it helps someone.
I realize this basically restates [PaulW2U]("http://ubuntuforums.org/member.php?u=1078994")'s advice, but it works, and it works nicely.. perhaps the step by step will be easier to follow.

Regards,
Rob

---


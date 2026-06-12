---
title: "Edit wiki page?"
date: 2014-03-12
forum: Forum Feedback &amp; Help
---

### Post by cogset on 2014-03-12
I'm posting here not knowing what would be the more appropriate place,so excuse me if this happens to be the wrong one:I think that in this wiki page [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) may be some inaccurate description,where it says 
> Removing a Hold

To remove a package from hold, you can run

sudo apt-mark unhold libxfont1 …

Replace 'libxfont1' with the package(s) you wish to unhold.

To see what the next version of the package is, use apt-cache policy packagename (see Debugging Package Priorities above).

Dpkg

**To remove pin from Dpkg:**

    Open a terminal
    sudo -s and hit enter
    Enter your password for sudo

    echo libxfont1 install | dpkg --set-selections
[B]
    Replace libxfont1 with the package you want to pin[/B]

it should probably say 

> **Replace libxfont1 with the package you want to unpin**

or may be it should be like:

```
**To remove pin/hold from Dpkg** 
```

instead of ```
[B]To remove pin from Dpkg
[/B]
```

and ```
**Replace libxfont1 with the package you want to unpin/unhold** 
```

instead of ```
**Replace libxfont1 with the package you want to pin**
```

anyways,it used to be that by logging with a launchpad account you could edit the wiki pages,but now the wiki login redirects to the new Ubuntu login and,furthermore,the page is tagged as Immutable-so there's nothing I could do about it.

---

### Post by Doug S on 2014-03-12
Please have a look at [this]("https://help.ubuntu.com/community/WikiGuide/Registration") page and [this ]("http://ubuntuforums.org/showthread.php?t=2208274")thread. Your issue is a recurring one, somehow it needs to be easier for people to be able to edit wiki pages. Please report back how you make out.

---

### Post by cogset on 2014-03-24
It really should be easier to do this:in the past I've logged in using my launchpad account,but now trying to log in that launchpad account using my new SSO login (as advised in one of the links above) doesn't work.

---


---
title: "How to get a Transparent Console/Terminal?"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by goonies on 2007-10-08
OK guys I need your help.

How would I go about getting a fully transparent terminal planted onto my desktop permanently?

I'd also like this terminal to automatically run irssi which would autojoin a channel. 

Thanks for your help guys.

---

### Post by jimerickso on 2007-10-08
try this website it worked for me!

[http://ubuntu-unleashed.blogspot.com/2007/08/howto-completely-transparent-shell-on.html](http://ubuntu-unleashed.blogspot.com/2007/08/howto-completely-transparent-shell-on.html)

---

### Post by multi on 2007-10-08
I recommend this [thread](http://ubuntuforums.org/showthread.php?p=3254093), That is basically the updated howto mentioned by jimerickso. It worked for me, looks pretty cool!

---

### Post by alwiap on 2007-10-08
> **multi said:**
> I recommend this [thread](http://ubuntuforums.org/showthread.php?p=3254093), That is basically the updated howto mentioned by jimerickso. It worked for me, looks pretty cool!

Yea that thread helped me do it in about 5 minutes and its fully customizable and easy to do.

---

### Post by goonies on 2007-10-09
I don't use Compiz Fusion and don't need a true transparent terminal since I want it planted to the desktop background.

Thanks though.

---

### Post by Forlong on 2007-10-09
> **goonies said:**
> I don't use Compiz Fusion and don't need a true transparent terminal since I want it planted to the desktop background.
Then all you need is **devilspie** (it's in the repos).

I wrote a How-To for that about a year ago. If you want, I'll look if I can find it tomorrow (it's in german but I guess I can translate the important parts for you).

---

### Post by smartboyathome on 2007-10-09
Here is the initial howto by jinacio which uses devilspie.
[http://ubuntuforums.org/showthread.php?t=202249](http://ubuntuforums.org/showthread.php?t=202249)

---

### Post by Subban on 2007-10-12
Install Eterm from the repo's, then perhaps add a launcher on the toolbar containing with this setting:

```
Eterm --trans -x --shade=0 --scrollbar=0 --buttonbar=0 --geometry=80x15+0+790 --foreground-color=white --color4 rgb:94/43/25 --color5 rgb:b0/b0/ff -F  -artwiz-smoothansi.de-medium-r-normal--13-130-75-75-m-60-iso8859-1
```

Ust Alt+left mouse to drag it around, change the size/location it opens at the -geometery option.
atm it is 80 wide, 15 deep, x=0 y=790.... lower left corner.

Get more info on what its doing from :
[http://linuxgazette.net/issue51/livingston-blade.html](http://linuxgazette.net/issue51/livingston-blade.html)

I also use this like you want to, running Irssi inside on the desktop, I can help with that if necessary but its pretty easy to setup..

Consider using it inside a screen too. The advatage of using screen is you kind of get Tabs, and you can auto start whatever apps you want in there (~/.screenrc I think is where) and flick between them, for me I have Irssi, Hellanzb and a spare Terminal running, Ctrl+a then a number jumps between them, invisible tabs in an invisible term ;)

[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)
[http://gentoo-wiki.com/MAN_screen#lbAF](http://gentoo-wiki.com/MAN_screen#lbAF)

Running Devilspie etc is more than needed for this simple job.

---


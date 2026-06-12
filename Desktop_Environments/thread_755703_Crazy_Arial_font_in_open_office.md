---
title: "Crazy Arial font in open office"
date: 2008-04-15
forum: Desktop Environments
---

### Post by jimmyxx on 2008-04-15
Hi all, I've attached an example of how my documents open up as in open office. 

This has only recently happened since upgrading to Hardy but I've seen it do this before. I can't find this font that its using anywhere in my /usr/share/fonts so not sure how to fix it. Any suggestions would be greatly appreciated.

Thanks

---

### Post by munkyeetr on 2008-04-15
Check to see that a font replacement hasn't been applied for some reason:

1) Open OO Writer
2) **Tools** -> **Options**
3) Under the main **OpenOffice.org** section, click on **Fonts** and check the replacement table.
4) Also under the** OpenOffice.org Writer** section, click on **Basic Fonts** and make everything looks OK there.

---

### Post by jimmyxx on 2008-04-15
I've checked theres nothing in the font replacements table.

In the Basic Font settings the heading was set to: IcedEarth so i've changed it to Arial.

When I'm using font drop-down (i've attached a screenshot), the Arial font is actually rendered as the IcedEarth font. I've searched through my /var/user/fonts/ and the Arial.ttf looks fine when opened in font viewer so I don't understand why it getting it mistaken for the icedEarth?

Thanks

---

### Post by munkyeetr on 2008-04-15
Yeah, that's weird. I'm not sure what else to suggest, hopefully someone else will come along who has run into this before. Sorry.

---

### Post by dai_vernon on 2008-04-15
I don't have much experience with this specific kind of problem, but it looks like the space Arial is being stored is being stepped on.  Have you tried uninstalling font packages and seeing if Arial becomes normal again?

Basic I know, but maybe?

---

### Post by jimmyxx on 2008-04-16
Thanks guys for you help, it was as simple as removing the icedEarth font. No idea whats up with it. Every time I make the fon't available the open office arial font gets replaced. I've attached the font here incase anyone wants to have a play. I'll also send it to the openoffice team to look at.

Thanks again!

---


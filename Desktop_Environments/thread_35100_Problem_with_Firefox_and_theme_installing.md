---
title: "Problem with Firefox and theme installing"
date: 2005-05-17
forum: Desktop Environments
---

### Post by shufla on 2005-05-17
Hello,

I've used general.useragent.vendorSub=1.0.4 in about:config to workaround problem with firefox version on mozilla.org sites. After then I wanted to install theme minifox  theme.

Well, it's listed here [1] [https://addons.mozilla.org/themes/showlist.php?application=firefox&numpg=10&pageid=6](https://addons.mozilla.org/themes/showlist.php?application=firefox&numpg=10&pageid=6)
and it's descriptive page is here: [2] [https://addons.mozilla.org/themes/moreinfo.php?application=firefox&numpg=10&id=607](https://addons.mozilla.org/themes/moreinfo.php?application=firefox&numpg=10&id=607)

That's funny/scary, beacause I wasn't able to install it from [1] when clicking on "Install it" link (file-roller was suggested to open .jar file), while from [2] "Install it" run fine.

What I was smoking/drinking? It's bug on mozilla page, something wrong with mozilla-firefox package or...magic? (link to .jar file is same from [1] and [2]).

I'm curious about that issue, please help me track that problem.

Some info:
shufla@atari:~$ dpkg -l mozilla-firefox | egrep ^ii
ii  mozilla-firefo 1.0.2-0ubuntu5 lightweight web browser based on Mozilla

---

### Post by jodef on 2005-05-17
I could be mistaken but the workaround was actually for the 1.04 backported version of Firefox I am not sure it will work with previous versions at any rate you're opening up yourself to serious security issues by doing that. If you really wan t to get the theme download the jar file and then open Firefox and the themes window and drag the jar file to the themes window. That's it your new theme is now installed.

---


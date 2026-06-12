---
title: "Copy packages/elinks/consolefont/mp3 player"
date: 2006-05-05
forum: Desktop Environments
---

### Post by xerxesv5 on 2006-05-05
Hi All,

I can't seem to find any useful answers to these...

- Additional packages weren't copied to disk (from the CD) during the install, anyone know a simple way to do that from console?

- elinks (console browser) has some wierd text corruption issue, where it leaves letters from previous UI "windows" or pages on screen. If I can't fix this, is there any way of getting proper "links" without compiling from source?

- any simple/efficient console-mode mp3 player that someone can recommend?

- I forget how to change the console font, and also to then persist that change for the next reboot.


Thanks in advance!

---

### Post by louis_nichols on 2006-05-05
[QUOTE=xerxesv5]Hi All,

I can't seem to find any useful answers to these...

- Additional packages weren't copied to disk (from the CD) during the install, anyone know a simple way to do that from console?[/QUOTE]

you don't really need to do that. After installing a system, it is best to make further installs from the online repos. Partly because, after upgrades, you will have certain version dependencies, so packages from the cd won't fit anymore. Also because it's just better to have the latest version of a package

If you really want to copy the packages... well, name a way! command line for copy is *cp*. You can use mc, a norton-commander like app. Or one of the many GUI file managers.

[QUOTE=xerxesv5]- elinks (console browser) has some wierd text corruption issue, where it leaves letters from previous UI "windows" or pages on screen. If I can't fix this, is there any way of getting proper "links" without compiling from source?[/QUOTE]

did you try to see if the repos don't have a better version? If they don't, the only better solution I can think of is to use lynx, alo a CLI browser. I haven't used elinks so I dunno differences between them

[QUOTE=xerxesv5]- any simple/efficient console-mode mp3 player that someone can recommend?[/QUOTE]
mp3blaster

[QUOTE=xerxesv5] I forget how to change the console font, and also to then persist that change for the next reboot.[/QUOTE]

sorry, dunno!


[QUOTE=xerxesv5]Thanks in advance![/QUOTE]
You're wellcome! Hope it helped

---


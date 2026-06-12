---
title: "Adding a menu entry with a custom command"
date: 2015-04-19
forum: Desktop Environments
---

### Post by Jakub_Sygnowski on 2015-04-19
Hello,
I have already struggled for a few times with adding a menu entry in lubuntu with a custom command, without success.

Concretely right now I have a two versions of chrome: A (which is default one) and B (which I compiled). Both work when I start them from the commandline.
I created two alternatives for `/usr/bin/chromium`:
```

update-alternatives --config chromium 
There are 2 choices for the alternative chromium (providing /usr/bin/chromium-browser).

  Selection    Path                                               Priority   Status
------------------------------------------------------------
  0            /home/sygi/projekty/chrome/src/out/Release/chrome   1         auto mode
* 1            /home/sygi/projekty/chrome/src/out/Release/chrome   1         manual mode
  2            /usr/bin/chromium-browser-orig                      1         manual mode

```
I can choose between them and the correct one runs when I type 'chromium-browser' to the terminal.
But when I click the button in the menu, it only starts the browser when it is the default one (2). When currently alternatives is set to 1 it doesn't do anything. I also tried setting Terminal=true and X-KeepTerminal=true, but anyway nothings appear there.

I will be glad for suggestions of the answer for this issue (or other things to check), as I already had similar issues with other created-by-me commands.

---

### Post by Rex Bouwense on 2015-04-19
As you know, editing the menu in Lubuntu is a little different.
[https://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/](https://lkubaski.wordpress.com/2012/06/29/adding-lxde-start-menu-and-desktop-shortcuts/)
[https://lkubaski.wordpress.com/2012/11/02/adding-lxde-start-menu-sections/](https://lkubaski.wordpress.com/2012/11/02/adding-lxde-start-menu-sections/)
[http://lxlinux.com/#9](http://lxlinux.com/#9)
Those are three web sites that I have found useful.

---

### Post by kerry_s on 2015-04-19
install menulibre for easy menu tweaking/editing.

sudo apt-get install menulibre

---

### Post by jesse27 on 2015-04-21
I quite like Ezame
[ATTACH=CONFIG]261446[/ATTACH]

---

### Post by kerry_s on 2015-04-21
> **jesse27 said:**
> I quite like Ezame
[ATTACH=CONFIG]261446[/ATTACH]

not in the repo's. you have to add a ppa. they have the exact same functions.

---


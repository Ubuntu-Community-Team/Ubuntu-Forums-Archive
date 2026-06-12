---
title: "N64 emulator ?"
date: 2014-11-05
forum: Emulators
---

### Post by michael-piziak on 2014-11-05
Is there a N64 emulator that works good?

---

### Post by adec2 on 2014-11-08
This should be under the emulators section but yes there is an emulator, mupen64plus

---

### Post by michael-piziak on 2014-11-08
> **adec2 said:**
> This should be under the emulators section but yes there is an emulator, mupen64plus

Hmm, I installed it from the Software Center and it didn't show up anywhere on the dock or even if I searched for it from Dash Home

???

---

### Post by westie457 on 2014-11-08
Install 'mupen64plus-ui-console as well. It should then be visible in the Dash.

---

### Post by ibjsb4 on 2014-11-08
I'm not a gammer, but found this.

[http://ubuntuforums.org/showthread.php?t=1998512&page=2&p=12007087#post12007087](http://ubuntuforums.org/showthread.php?t=1998512&page=2&p=12007087#post12007087)

[http://ubuntuforums.org/showthread.php?t=1993047&p=12297228#post12297228](http://ubuntuforums.org/showthread.php?t=1993047&p=12297228#post12297228)

---

### Post by deadflowr on 2014-11-08
> **westie457 said:**
> Install 'mupen64plus-ui-console as well. It should then be visible in the Dash.
This is already installed, it's a dependency of mupen64plus, and it is only a command line frontend:(.

mupen64plus used to have a really, really, really good user interface >> prior to version 1.99.
To get mupen64plus to work now you need to either learn how to use the command line interface, or install a third-party graphical frontend.

If you are willing to learn how to use the command line simply open a terminal and type mupen64plus --help.
It has a lot of options, but basically like most commands, if you simply run the command as
```
mupen64plus the-path-to-the-game
```
replacing the-path-to-the-game with the actual path to your game 
It'll run the game, though it has odd defaults (resolution I think is small 600x400 or something, and the controllers are usually very odd as well, among other things you might not like.), so if you go this route you would need to figure out the best options to use, which can be either a frustrating or uplifting experience.

Now, the second option is probably the better option, and the best I have found of third-party user interfaces is mpy64.
It is not available in the software center,( that I know of, but can be install through a download from here
[http://m64py.sourceforge.net/](http://m64py.sourceforge.net/)
You can also look at a few others, here
[https://code.google.com/p/mupen64plus/wiki/ThirdPartyPlugins](https://code.google.com/p/mupen64plus/wiki/ThirdPartyPlugins)
but chances are m64py will suit you fine.

So, IMO, unless you really want to fuddle with commands, go for the m64py interface.

Hope it helps.

---


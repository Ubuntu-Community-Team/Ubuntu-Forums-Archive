---
title: "compiz plugins always revert to disabled"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by Hoaxe on 2007-11-01
I have this problem on my laptop with the compiz effects where when i try to enable one of the plugins, like neg for instance, or ring switch, they automatically disable themselves.

my laptop is an HP laptop that my dad (an hp reseller) put together for me. i have had no kinks with it worth mentioning except for this one because i thought it was a keyboard problem for the following reason:

the effects that i can not enable all involve the super key. i though it was a keyboard problem, but after checking for the keyboard settings and what not, i found the window where when you press on a key the associated key on the on-screen keyboard turns blue. so i know it's not a keyboard problem. 

also, when i plug a mouse, i can zoom in by pressing the super key and scrolling, so i know that works, I just don't understand why none of the other super key effect work?

I also tried mapping the keys to something else other than the super key and the effect still disables, it's like i don't have the effect or something like that. i checked the repo and the compiz package itself is not grayd in. the main plugins as well are not grayd in. however the extra plugins are grayed in. Is there a package i should be having that i do not have?

i read that some people were having super key issues and when they download emerald or some other trivial thing it started working again, well i already have emerald, in fact i'm using it right now. 

I also tried enabling the options through advanced preferences, unchecking the box in that tab and manually putting some of the effects in the running applets -- they would all just reset just the way they did when i was using the regular method.

thanks for the help as usuall

EDIT: it's a fresh gutsy install BTW

---

### Post by rogeriovinhal on 2007-11-02
I have the same problem as you do. I have a problem if the 'put' plugin is not checked, the windows always are created far up in the screen, so I can't see the buttons to maximize, close or minimize. So I have to move them down to make anything.

If I check the put plugin and check the 'smart' window placement, everything is fine, but time to time it disables itself alone.

This is very picky, I hope a solution comes out.

---

### Post by Zorael on 2007-11-02
I had some issues activating certain options in some plugins, but this was **completely solved** by switching to a flat-file configuration backend. This is not the default. Your mileage may vary, though, but this worked for me.

You'll want to export your profile first so as not to lose your setup.

[INDENT]Settings Manager -> Preferences -> Export, save someplace
Backend -> Flat-file Configuration Backend
Import -> your saved file[/INDENT]

Furthermore, if you're launching Compiz through a launcher (such as from the Sessions options in Ubuntu, Autostart folder in Kubuntu, or any launcher anywhere), add 'ccp' as an argument. This will (supposedly?) make Compiz use its own configuration format. Or so I believe I've read. Someplace.

It can't hurt though, right?

For instance, I launch it by:
```
$ compiz --replace --loose-binding --ignore-desktop-hints ccp
```

Loose bindings almost always yield better performance on Nvidia cards.
Ignore desktop hints helps when, especially in KDE, you end up with way more virtual desktops than you set it up to have. (I ended up with 16 instead of four)

---

### Post by Hoaxe on 2007-11-02
> **rogeriovinhal said:**
> I have the same problem as you do. I have a problem if the 'put' plugin is not checked, the windows always are created far up in the screen, so I can't see the buttons to maximize, close or minimize. So I have to move them down to make anything.

If I check the put plugin and check the 'smart' window placement, everything is fine, but time to time it disables itself alone.

This is very picky, I hope a solution comes out.

touchee on that, i get the same problem, but it's not constant - sometimes i get and sometimes i don't. one this is for sure, it's annoying all around.

will try suggested suggestions.

---

### Post by rogeriovinhal on 2007-11-10
Actually, today I noticed something.

From time to time compiz starts behaving very strange, like can't move windows, windows decorations doesn't appear, some effects don't work...

When this happens, I make it work again selecting "extra effects" on Appearance Menu and then I go back to "Custom Effects". Then everything works fine, but SOME compiz settings disable themselves.

Does that happen to you also? How can we make it stop to have this strange behaviour from time to time?

---


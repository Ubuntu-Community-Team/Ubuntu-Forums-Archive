---
title: "Some beryl Window Decorations missing"
date: 2007-03-19
forum: Desktop Effects &amp; Customization
---

### Post by impactdni on 2007-03-19
Running Beryl on a Radeon on Feisty.

Some of the window decorations work just fine, some of them don't.

My terminals open with the correct window decorations, but as soon as it gets maximized, the window decorations just turn into white strips.  The buttons are still there, I can mouse over them, but the colors/graphics are gone.

Some programs don't show the decorations at all, regardless of being maximized/normal.  Two such examples are Firefox and Nautilus.  However, nautilus popups (such as the "about" window) show the correct borders.

Anyone heard of this?

Any ideas?

---

### Post by Yoooder on 2007-03-22
I've seen issues that are somewhat similar that seem to be related to specific themes.  Try switching your themes and see if it's constant across all of them, or maybe just specific to a certain rendering engine...

---

### Post by josephus on 2007-03-23
I have been having a similar problem running Edgy Eft with a Radeon 7500 Mobility chipset.  I can get rid of the white borders when maximized by disabling EXA acceleration in the xorg.conf file and using the standard XAA mode.

Other people have been able able to keep EXA by adding  /etc/drirc file specifying it to allow large textures, but it hasn't worked for me.  Just search beryl + drirc and you should be able to get a couple of hits with more details if you want to give it a try.

---

### Post by impactdni on 2007-03-26
Yep, seems to solve the problems.
The drirc fixed it.  Thanks a ton guys.

(For the help of others, add the following to /etc/drirc)
```
<driconf>
    <device screen="0" driver="radeon">
        <application name="all">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>
```

---


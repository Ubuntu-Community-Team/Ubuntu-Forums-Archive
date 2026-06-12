---
title: "Feisty Font Frustrations"
date: 2007-07-25
forum: Desktop Environments
---

### Post by Tamale on 2007-07-25
Hello all,

I don't like the way fonts look in feisty.. the exact same fonts that looked great in edgy..

Let me just say that I tried looking at the other long thread about a newer font autohinter for feisty here: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670).

The problem I'm having doesn't have anything to do with sub-pixel smoothing though, far as I can tell anyway..  the way the good 'ole "Sans" looks (Bitstream Vera Sans, I guess?) just looks like it's rendered completely differently to my eyes in the two distros.

Here's a screencap from edgy in firefox that showed the beautiful Sans font off perfectly, imo:
[http://tigger.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png](http://tigger.uic.edu/~jbuss2/pics/ubuntu/fontsEdgy.png)
The font setting in firefox is Sans, 16 pt.  Nothing else.  I never installed any custom font shtuff and didn't do anything different except select the sub-pixel algorithm I liked best.. ("slight" i think)

Notice especially how the bolded titles for sections in the google page aren't THAT much bolder than the rest of the text, and the 10 pt sans font in the font preferences window is sharp as a tack.

Now here's a shot from feisty:
[http://tigger.uic.edu/~jbuss2/pics/ubuntu/feistySans.png](http://tigger.uic.edu/~jbuss2/pics/ubuntu/feistySans.png)

You've got to be blind to not see the difference.  The font preferences windows especially shows how this new sans is softer and each line is noticeably thicker, yet each letter is actually narrower than before as well.  In addition to the generally 'softer' look that I really don't like at all, bolded versions of fonts look ridiculously wide and bold.

Are these two separate problems?  (Blurriness and over-boldness)  How can I go about fixing them and just having the same Sans I had in edgy?

---

### Post by Tamale on 2007-07-26
bump?

---

### Post by gcarrillo on 2007-08-21
I'm seeing a similar issue too...although I also saw that letters on iGoogle, for example, were slightly horizontally compressed.  The letter 'o' didn't look round, and instead looked "taller" than it should have.  The following did the trick for me:
```

sudo dpkg-reconfigure fontconfig-config

```
and choose 'Autohinter, Always, No', instead of 'Native, Always, No' as was suggested by [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670). Then:
```

sudo dpkg-reconfigure fontconfig

```

---


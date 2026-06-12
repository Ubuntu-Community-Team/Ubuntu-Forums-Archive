---
title: "netbeans and eclipse font issue"
date: 2009-08-05
forum: Desktop Environments
---

### Post by bor_1 on 2009-08-05
I have Ubuntu 9.04, Netbeans 6.7 and Eclipse 3.5 I'm working on laptop. Problems is that the same font looks different on this java IDEs. Look at this screen: [http://img5.yfrog.com/img5/5466/screenshotlcz.png. ]("http://img5.yfrog.com/img5/5466/screenshotlcz.png")
It shows how the same fonts looks on NB (left side) and Eclipse. Eclipse font seems too smooth, too bold, too antialiased. I would like have same font look in Eclipse as i have now in NB.

Few more screens:
[http://img142.yfrog.com/img142/7792/screenshot1prf.png](http://img142.yfrog.com/img142/7792/screenshot1prf.png) - eclipse on my computer
[http://klomp.org/mark/classpath/generics-native-eclipse-jamvm.png](http://klomp.org/mark/classpath/generics-native-eclipse-jamvm.png) - eclipse on other computer - found in internet (and this font look i would like acomplish on my computer)
[http://img165.yfrog.com/img165/5451/screenshotjavaapplicati.png](http://img165.yfrog.com/img165/5451/screenshotjavaapplicati.png) - NB on my computer. (fonts are quite similar to previous screen)

I noticed that similar problem concerns also other programs:
[http://img188.yfrog.com/img188/6083/screenshot3b.png](http://img188.yfrog.com/img188/6083/screenshot3b.png) - CodeBlocks fonts looks pretty same as Eclipse fonts, and Emacs font style is very similar (if no the same) to NB.

I'm computer programmer and i started recently using linux so font issue is very important for me, i would love have current Emacs and NB font style in all programs (or at least in Eclipse) but i have no idea how to acomplish it.

I came out with conclusion that majority programs in my system(eclipse, codeblocks, gedit .....) have inherited font setting in exact way from my system.
Here are my system font settings: [http://img514.yfrog.com/img514/4583/screenshot4h.png .]("http://img514.yfrog.com/img514/4583/screenshot4h.png")
This doesn't mean that NetBeans font setting are  independent of system settings. Changes in system font setting also affect fonts in NetBeans but they still different and much more nicier.
As you can notice the only clear difference i can acomplish by disabling smoothing. But in that case they will look very ugly.
Look also here: [http://img7.yfrog.com/img7/6779/screenshot5fns.png](http://img7.yfrog.com/img7/6779/screenshot5fns.png).
On the left is font setting window i found somewhere on the internet (i guess this is how this windows is supposed to look), on the right is my font setting window. Shouldn't they look the same ? First noticeable difference is that on my screen fonts are bolder. I don't them to look  this way.

Summing up i would like have the same font look in Eclipse as i have now in NB. Furthermore i think that i have more general problem what proves last screen showing that my fonts in system are bolder and simply looks different. I definitely dont them to look this way.
What i most want is to have the same fonts style in all programs as i have now in Netbeans or Emacs, it would be perfect but i suspect it would be tot beautiful to be true :)

---

### Post by benny.deng on 2010-02-19
I have the same problem, eager for anyone's  help

---

### Post by debian_andy on 2010-03-26
There's no solution as there actually is no problem!
Eclipse as Aptana IDE are Java applications that use their own fonts.
Netbeans is however also a Java applications, but it uses GTK, which results in better fonts and integration with your Desktop (themes).

---


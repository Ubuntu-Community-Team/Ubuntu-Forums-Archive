---
title: "Help with xmodmap"
date: 2007-07-21
forum: Desktop Effects &amp; Customization
---

### Post by Aleksandersen on 2007-07-21
Hi,

I reallt does not understand how to use xmodmap. Can someone please explain it to me? I have scanned the manual pages and seen some examples, but that did not help much....

The characthers I miss the most are:
- = - (hypen)
Alt Gr + - = &#8211; (en dash)
Alt Gr + Shirt + - = &#8212; (em dash)
Alt Gr + . = &#8230; (horizontal ellipsis)
Alt Gr + Å = &#9608; (full block)

I also need a way (preferably something like Alt Gr + f and i) to type:
ct (ligature &#8216;ct&#8217; - made up by U+63 U+200D U+74)
&#64256; (ligature &#8216;ff&#8217;)
&#64257; (liagure &#8216;fi&#8217;)
fj (ligature &#8216;fj&#8217;)
&#64259; (ligature &#8216;ffi&#8217;)
&#64260; (ligature &#8216;ffl&#8217;)
&#64258; (ligature &#8216;fl&#8217;)
&#307; (ligature &#8216;ij&#8217;)
&#64262; (ligature &#8216;st&#8217;)

---

### Post by anupamsr on 2008-02-27
Hi! I know this is a very old thread, but if you are still around, can you tell me if you got this problem corrected? (I am sure you did, if you are still around :) )

---

### Post by digitalbenji on 2008-02-27
Hi,
   Just coming across this thread on my daily peruzal of the forums.
   For those unaware, xmodmap and xev display the internal codes that the computer interprets when you press a key/button on your computer.  So, this means if you have a button you want remapped, or a button that isn't doing anything, you can use these default X windows utilities to help yourself out!  
   If you have a button that you want to test out, run this in terminal ```
xev
```  And see if xev picks up that you are pressing the button.  Keep in mind that xev reports every event, including movement of the mouse!
   If you want to customize your configuration, to change button mappings, or to bind actions to unbound buttons, you will want to create a file in your home directory called .Xmodmap and place the entries in there.  A good guide to doing this can be found here:  [http://http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html]("http://http://dev-loki.blogspot.com/2006/04/mapping-unsupported-keys-with-xmodmap.html")
   Xmodmapping keys can be extremely helpful.  I recall I had a laptop that incorrectly would send the kernel the keycode CL_ENTER instead of ENTER.  This meant I couldn't log in, but by remapping this with a .Xmodmap file, I was able to solve the problem.

Best Regards, Good Luck!

---


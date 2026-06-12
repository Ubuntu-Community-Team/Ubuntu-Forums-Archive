---
title: "xmodmap creates &quot;hidden&quot; extra layout"
date: 2009-05-14
forum: General Help
---

### Post by NimoTh on 2009-05-14
Hi there,

I'm on 9.04 Jaunty (problem was the same on 8.10 Intrepid).

My goal: two keyboard layouts: 
- one German layout with "<" and ">" where they are displayed on my German keyboard, which is to the right of the left shift key
- another US layout with the "\" and "|" keys where the "<" and ">" keys are displayed.

Here's the problem: I have two layouts set up in the layout preferences. With the WinKey (custom set up) I can change between the two. When I create a new custom layout, then I can suddenly change between three layouts using the WinKey. Like this: US -> Deu -> Deu. Yes, it seems there are two German layouts now but there are only two layouts displayed in the layout preferences (USA and Germany). Moreover, none of the German layouts behaves like one anymore regarding the "<>" key. On two layouts I have "\|", which is great. On the third one I have "||" (means 'bar' w/ and w/o shift), which is bad.

It looks to me like my best bet is just editing the original US keyboad layout. I looked at /usr/share/X11/xkb/symbols/us and de but I couldn't find how to tell the us layout that I want the "<>" keys remapped because the "<>" key is not listed.

Can someone please help me? It sucks to have to use the "\|" key next to the Enter key.

Thanks a lot in advance
Martin

---


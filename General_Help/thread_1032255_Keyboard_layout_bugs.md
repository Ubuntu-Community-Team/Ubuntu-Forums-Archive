---
title: "Keyboard layout bugs"
date: 2009-01-06
forum: General Help
---

### Post by flow_ca on 2009-01-06
Hi,
I have a really odd problem:
I use Ubuntu Intrepid Ibex, and I tried to change my keyboard layout via system-settings-keyboard. It is currently set to Germany eliminate dead keys.
Now when I change the layout to one in a language other to German, the following happens:
I open up a new xterm window and type in a few characters to test the layout. What I get when i type asdf is æßð&#273;, that is the 3rd characters for those keys (I'm not holding Alt Gr). When I change the layout back, I get my working German layout again.
Do you have any idea how that happens, and what to do about it?
Thanks in advance
Florian

---

### Post by flow_ca on 2009-01-06
For some reason it's working again, don't ask my how.
I removed my custom .Xmodmap, loaded a keyboard layout, put my Xmodmap back and loaded the layout i wanted, and it worked.
thanks anyways, and sorry
florian

---

### Post by flow_ca on 2009-01-06
For some reason it's working again, don't ask my how.
I removed my custom .Xmodmap, loaded a keyboard layout, put my Xmodmap back and loaded the layout i wanted, and it worked.
thanks anyways, and sorry
florian

---


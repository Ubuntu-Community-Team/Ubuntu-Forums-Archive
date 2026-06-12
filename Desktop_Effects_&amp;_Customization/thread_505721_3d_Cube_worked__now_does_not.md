---
title: "3d Cube worked / now does not???"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by ninja82 on 2007-07-20
I have seen a couple of posts about this problem - could someone please explain gconf-editor use so that I can correct my issues? I had the desktop cube working fine on my laptop (system / preferences / desktop effects). Now, after several updates the cube does not work - but the wobbly windows works fine. Sorry if this has been answered elsewhere, but I could not find a post that explained the "cure" in a way that I could understand.
Thanks for the help!
Bob

---

### Post by avik on 2007-07-20
You can find the gconf-editor by going to the terminal and typing in gconf-editor.  Then go to apps->compiz->general->screen0->options and set hsize to 4.

Tell me if any part of that is confusing and I'll be glad to explain in more detail.

---

### Post by ninja82 on 2007-07-20
Thank you much! I just did not know that I needed to type the gconf-editor in a terminal. Was looking all over for it in the menus (don't laugh - I am sure there was at least one other person out there that didn't know this too:))
The cube is back! 
Happy days...
Bob

---

### Post by avik on 2007-07-20
Yeah, it can be confusing to find certain programs.  I remember installing [The Widget Factory]("http://www.stellingwerff.com/?page_id=10") from the repos, but I just couldn't find the program to run it.  There was no program called thewidgetfactory installed on my system.  Turns out, the name of the binary was twf.

---


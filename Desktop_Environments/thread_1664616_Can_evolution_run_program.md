---
title: "Can evolution run program?"
date: 2011-01-11
forum: Desktop Environments
---

### Post by kaspar_silas on 2011-01-11
Hi All,

Hopefully someone can help me out with a slight evolution problem. I want a certain key word in a subject of a received email to kick off a program. But it just doesn't seem to work as it should. 

I did a little test by first making a simply pop up:
echo -e "zenity --info --text=\"TEST\"" > ~/bins/TESTER
chmod +x ~/bins/TESTER

I tested this and it was fine. I then added the evolution filter if subject contains TESTER change colour and Run Program ~/bin/TESTER.

Now if I send myself an email with the subject TESTER the colour does indeed change but there is no pop up. If I select the email and hammer ctrl+y (to reapply filters) loads of times it does eventually. But that's not exactly useful.

Has anyone any ideas what could be wrong?
O incidentally it's not the GUI aspect as I switched the pop up to just logging to a text file without any effect.

---

### Post by kaspar_silas on 2011-01-11
O if someone could try out the simple test on there system and report back it would be most appreciated.

---

### Post by kaspar_silas on 2011-01-12
Really no-one can help with the standard email client? That is a little disappointing.

---

### Post by Cheesehead on 2011-01-12
You may need to specify which display to put the zenity box into. Try:
DISPLAY=:0.0 zenity --info --text=\"TEST\"

---

### Post by kaspar_silas on 2011-01-12
Interesting I didn't know you could do that.

However unfortunately it didn't work. The problem is not the program as if I call it manually or through other scripts everything is okay.

It's that evolution just doesn't call the program. Well at least not repeatably. If I just sit and reapply the filter over and over then it will actually only call the program about every 5-10th try.

However if I change "run a program" to "change the text colour" or some other simple thing it runs every time.

---

### Post by irishbreakfast on 2011-01-13
I've not used that feature, maybe the folks at the mailing list can assist.
evolution-list -- General discussion and user queries of the Evolution
[http://mail.gnome.org/mailman/listinfo/evolution-list]("http://mail.gnome.org/mailman/listinfo/evolution-list")
Cheers

---

### Post by kaspar_silas on 2011-01-14
Cheers for that.

I'll have a chat with them and report back if I get a solution

---


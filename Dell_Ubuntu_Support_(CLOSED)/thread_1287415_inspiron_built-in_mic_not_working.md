---
title: "inspiron built-in mic not working"
date: 2009-10-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jaden93 on 2009-10-10
Alright, so i have a dell inspiron computer and i just switched over, though not completely, to ubuntu. I'm having issues with my mic. well to put it plainly it wont work. When i was on windows my mic worked fine and everything but on ubuntu it wont. i checked the volume settings, i tried changing the mixer, i even dowloaded skype to do the echo voice call thingy to see if there was a change (there wasn't one it still didn't work) so what ii want to know is, is there a way to fix this.  


---

PLZ HELP D:

---

### Post by mikewhatever on 2009-10-10
Personal experience taught me that quite often, the internal mic doesn't work simply because the external one is selected, and vise versa. You can select which one to use under Volume Control, Options tab. If you don't have such a tab, click on preferences and make sure the appropriate box is ticked.

---

### Post by jaden93 on 2009-10-10
I've done that and i still have no change. I went into the sounds in my system prefrences and i found that the mic plays on the oss-open sound system and when i test it it'll work but i still can't use my mic. 


---
no change

---

### Post by mikewhatever on 2009-10-10
And how exactly do you test it? Skype and similar programs also have sound settings that apply.

---

### Post by jaden93 on 2009-10-10
I tested it to ways. First i tested it on skype on the echo call then earlier today i went to 'systems > perefrences > sound' and tested out some of the sound capturers under devices. the oss sound capturer worked slightly when i tested it, it would work on one test but when i tested it once again it didn't work.

---

### Post by mikewhatever on 2009-10-11
Hm, I don't know. What model is your Inspiron, also, does the external mic work?

---

### Post by jaden93 on 2009-10-12
Dell inspiron 1525,  and yes my external mic works fine. Its just the internal mic thats having the trouble.

---

### Post by karamu on 2009-10-13
I don't know if it 's the same problem or not but I had a similar issue when I upgraded to 9.04 on my Mini 10v- the external mic stopped working. When I upgraded to Karmic though it resolved the problem.

---

### Post by Boondoklife on 2009-10-13
check in alsamixer, I had an issue before where the mic was set to anolog and needed to be digital

---

### Post by witeshark17 on 2009-10-13
I had this issue; it turned out to that the mic(s) were set to mute in the mixer control menu.

---


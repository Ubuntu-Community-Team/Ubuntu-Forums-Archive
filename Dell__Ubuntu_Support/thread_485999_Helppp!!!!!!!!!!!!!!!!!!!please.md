---
title: "Helppp!!!!!!!!!!!!!!!!!!!please"
date: 2007-06-27
forum: Dell  Ubuntu Support
---

### Post by weverjames on 2007-06-27
I JUST RECEIVED MY DELL DIMENSION LOADED WITH UBUNTU.  SO FAR IT IS RUNNING BUT I NEED TO ADJUST RESOLUTION TO 1680X1050, WHICH IS THE NATIVE RESOLUTION OF MY SCREEN.  THERE IS NO OPTION TO SELECT THAT RESOLUTION.
I FOUND SOME INSTRUCTIONS, HOWEVER I AM COMPLETELY NEW TO LINUX AND I DON'T UNDERSTAND SOME OF THEM.  COULD SOMEONE HELP ME STEP BY STEP?
i DON;T EVEN KNOW HOW TO USE A TEXT EDITOR TO DO IT.

---

### Post by mips on 2007-06-27
1. Stop screaming !
2. [http://ubuntuforums.org/showthread.php?t=479005]("http://ubuntuforums.org/forumdisplay.php?f=256")
3. [http://ubuntuforums.org/forumdisplay.php?f=256](http://ubuntuforums.org/forumdisplay.php?f=256)

---

### Post by DoctorMO on 2007-06-27
mips - how ironic, your avitar is 'the scream' by van gogh right?

---

### Post by phizikal on 2007-06-27
Chyeah, I noticed that.

---

### Post by mips on 2007-06-27
> **DoctorMO said:**
> mips - how ironic, your avitar is 'the scream' by van gogh right?

I don't see the irony, I'm not typing in caps.

It's Edvard Munch, [handy]("http://ubuntuforums.org/member.php?u=55341") has a Van Gogh avatar if I'm not mistaken.

---

### Post by Tundro Walker on 2007-06-27
The irony was that you told the OP to 1) stop screaming, yet your avatar is the screaming guy from that one painting by some dead guy.  (Would you believe I took Art History in college?  Yeah, neither would I...)

---

### Post by Fenryr on 2007-06-27
> **Tundro Walker said:**
> The irony was that you told the OP to 1) stop screaming, yet your avatar is the screaming guy from that one painting by some dead guy.  (Would you believe I took Art History in college?  Yeah, neither would I...)



Given that 'the Scream' was actually painted by Munsch (sp?) and not Van Gogh, I'm willing to believe you TOOK the course...I'm not so willing to believe you PASSED it...*l*

---

### Post by init1 on 2007-06-27
Very OT. Shouldn't this be in the "Absolute Beginners" section?

---

### Post by RAV TUX on 2007-06-27
> **mips said:**
> I don't see the irony, I'm not typing in caps.

It's Edvard Munch, [handy]("http://ubuntuforums.org/member.php?u=55341") has a Van Gogh avatar if I'm not mistaken.

I like this version of The Scream:

[[IMG]http://img167.imageshack.us/img167/4003/simpsonsscreamloei4.th.jpg[/IMG]](http://img167.imageshack.us/my.php?image=simpsonsscreamloei4.jpg)

---

### Post by RAV TUX on 2007-06-27
> **RAV TUX said:**
> I like this version of The Scream:

[[IMG]http://img167.imageshack.us/img167/4003/simpsonsscreamloei4.th.jpg[/IMG]]("http://img167.imageshack.us/my.php?image=simpsonsscreamloei4.jpg")

this one is cute too...
[[IMG]http://img244.imageshack.us/img244/8943/bunniesdoscreambymistercv5.th.jpg[/IMG]]("http://img244.imageshack.us/my.php?image=bunniesdoscreambymistercv5.jpg")

Here is another interesting version(caution this could be considered adult material by some fine art by others):
[http://img244.imageshack.us/img244/8486/thegoatsescreambigwr3.jpg](http://img244.imageshack.us/img244/8486/thegoatsescreambigwr3.jpg)

This version of The Scream, looks vaguely familiar:
[[IMG]http://img187.imageshack.us/img187/5808/dubyascream2bu6.th.jpg[/IMG]]("http://img187.imageshack.us/my.php?image=dubyascream2bu6.jpg")

---

### Post by spockrock on 2007-06-27
> **weverjames said:**
> I JUST RECEIVED MY DELL DIMENSION LOADED WITH UBUNTU.  SO FAR IT IS RUNNING BUT I NEED TO ADJUST RESOLUTION TO 1680X1050, WHICH IS THE NATIVE RESOLUTION OF MY SCREEN.  THERE IS NO OPTION TO SELECT THAT RESOLUTION.
I FOUND SOME INSTRUCTIONS, HOWEVER I AM COMPLETELY NEW TO LINUX AND I DON'T UNDERSTAND SOME OF THEM.  COULD SOMEONE HELP ME STEP BY STEP?
i DON;T EVEN KNOW HOW TO USE A TEXT EDITOR TO DO IT.

one repress the cap locks or release the shift key. two wrong section, three try install 915resolution package from synaptic.

---

### Post by OzzyFrank on 2007-06-28
To edit the xorg.conf text config file:

sudo gedit /etc/X11/xorg.conf

You will see some sections with screen sizes repeated a few times... just add the missing resolutions there, ending in the highest you want (like my screen/video card can go beyond 1600x1200 but I never use over that, so I've limited my settings to that size as max).

---

### Post by OzzyFrank on 2007-06-28
> **spockrock said:**
> one repress the cap locks or release the shift key. two wrong section, three try install 915resolution package from synaptic.

Well, he can be forgiven for putting this in the Dell section, since he just got a Dell, and to him the issue is with the company (right or wrong). I'm very interested in this whole Dell-Ubuntu thing, and am looking forward to seeing what people (probably newbies in particular) think of it. I've recently read Dell are only putting Ubuntu on their notebooks that are the thickest and heaviest, or else have less features than basically the same model running Vista. That kinda sucks.

I gather these PCs use an Intel graphics chip or whatever, as 915resolution is only for Intel, correct?

(PS: About the screaming, at least he didn't bold and underline them as well, hehe. But seriously, as a tutor, I've seen so many people that hit the caps lock for the first letter then just leave it, thinking it's ok... meaning they have absolutely no idea the rest of us see them as screaming... I had a mate that screamed every sms message he ever sent, hehe... and when I'd tell him to stop yelling, he would be like "Oh, yeah, sorry, I forgot!". So if you ever tell someone to stop screaming, and they're like "What do you mean?", they ain't messin' with you - they seriously have no idea typing in capitals is considered yelling and that it aggravates the more sensitive among us)

---

### Post by mips on 2007-06-28
> **OzzyFrank said:**
> 
(PS: ... So if you ever tell someone to stop screaming, and they're like "What do you mean?", they ain't messin' with you - they seriously have no idea typing in capitals is considered yelling and that it aggravates the more sensitive among us)

I'm probably going to get an infraction for this but here goes anyway. If he read the code of conduct when he signed up he would have seen:

> 10. Please strive to communicate with other users as effectively as possible:[LIST=1][LIST]
[*]Please do not write posts in all uppercase letters, as it looks as if you are screaming at the people reading your post.[/LIST][/LIST]

---


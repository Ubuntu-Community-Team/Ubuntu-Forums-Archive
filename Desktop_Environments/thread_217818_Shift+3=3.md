---
title: "Shift+3=3"
date: 2006-07-17
forum: Desktop Environments
---

### Post by lwr on 2006-07-17
When I do shift+3 i get 3. It should be a pound sign. As far as i can tell my keyboard layout is correct other than that. Any suggestions?

---

### Post by ishimaru_kaito on 2006-07-25
Argh! Me too!  Yet on my laptop - a pound sign.  How in tarnation?!?!?!
:-k :-k

---

### Post by ishimaru_kaito on 2006-08-06
I had to do a reinstall and now my £££ sign works.  Argh! ](*,)

---

### Post by GazzaK on 2006-08-11
this is the same as i'm getting, but I don't want to reinstall, any ideas?

---

### Post by lwr on 2006-08-31
I'm sure there must be an easier solution than reinstalling. Do none of you Ubuntu experts out there have any idea what we need to do?

---

### Post by Dramist on 2006-08-31
since i was reinstalling i did a little test, try using British English as your keyboard layout.

---

### Post by its_me_gb on 2006-08-31
i've had the same problem, a little searching on these very forums bought me:

```
xmodmap -e 'keycode 12 = 3 sterling'
```

and what can i say... £££££

george

---

### Post by lwr on 2006-08-31
Excellent! Thanks george. I knew the solution would be simple. Just a case of knowing what to do. Thanks again.

Luke

---

### Post by lwr on 2006-09-04
OK slight problem - using "xmodmap -e 'keycode 12 = 3 sterling'" only lasts for the current session. I tried putting it in startup programs, but that doesn't seem to work. Any ideas?

---

### Post by someusernoob on 2006-09-04
Do:
```

cd /usr/bin
gksudo gedit sterling

```

Now you see an empty file, put this in it:

```

#!/bin/bash
xmodmap -e 'keycode 12 = 3 sterling'

```

and save the file.

Make it executable:

```

sudo chmod 755 sterling

```

Now put 
```

sterling

```
into your sessions menu (startup programs), and it will do the command on start up.

And finally type 
```

cd

```
to go back to your home folder.

/edit: i named the file sterling, but you can name it whatever you want of course.

---

### Post by lwr on 2006-09-05
Thanks for that someusernoob. I had a little trouble getting it to work, because you missed off the end quote after 'keycode 12 = 3 sterling' (I should really look at what I type instead of blindly cutting and pasting). It all works fine now though, so thanks for your help.

---

### Post by someusernoob on 2006-09-05
Oh :P im sorry. I really didnt notice that i copy/pasted it wrong. I fixed it now for those who need it.

---


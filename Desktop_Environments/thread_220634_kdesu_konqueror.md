---
title: "kdesu konqueror"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Freddy on 2006-07-21
Hi all.

When I try to "kdesu/sudo konqueror" I can't browse any files, I'll get a "failed to comunicate with klauncher" message. Any ideas of what to do?   /// Freddan

---

### Post by Freddy on 2006-07-22
bump

---

### Post by Freddy on 2006-07-22
bump

---

### Post by aysiu on 2006-07-22
You definitely shouldn't do ```
sudo konqueror
```

Always use ```
kdesu
``` with graphical applications.

Does ```
kdesu
``` work with anything else? For example, what happens if you do ```
kdesu kcontrol
```?

Also, does regular *sudo* work with terminal applications? ```
sudo aptitude update
``` for example?

P.S. [It's not looking good for the home team.](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=%22failed+to+communicate+with+klauncher%22&btnG=Search)

---

### Post by Freddy on 2006-07-22
Yeah I know that I should use "kdesu kde graphical program" I just wanted to eliminate all "sudo" posts :-).

ahh thx I found out that the problem lays within kdesu somehow, what happens is kind of hard to explain, but when using it to open a konqueror I get a "failed to communicate with klauncher" message. 

After reading your post I tried with "kdesu kcontrol", the app starts just fine but at the "welcome" screen there's not any background picture, like it should. Even of all the "head" tabs the graphics seems wrong or missing, the undertabs works fine though.

When trying "kdesu kate" it boots but I get the "failed to communicate" message there to but I can use it after clicking it away, which I can't with konqueror.

Thx for all the help I can get, cause this is real annoying ,-).   /// Freddan

---

### Post by aysiu on 2006-07-22
What about when you do this? ```
sudo -s
konqueror
```

---

### Post by Freddy on 2006-07-22
I'll still get that bloody "failed to communicate with klauncher" message, I even tried a reinstall of sudo no change with that either :-(.   /// Freddan

---

### Post by Freddy on 2006-07-23
bump

---


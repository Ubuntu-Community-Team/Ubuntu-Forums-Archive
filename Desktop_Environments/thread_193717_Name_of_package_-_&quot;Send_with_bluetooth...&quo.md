---
title: "Name of package - &quot;Send with bluetooth...&quot;"
date: 2006-06-10
forum: Desktop Environments
---

### Post by daller on 2006-06-10
Hi There,

When I want to send a file using bluetooth, I rightclick the file choose: "Actions -> Send with bluetooth..."

What's the name of the package that it opens? (kbtobexclient?)

The reason I'm asking, is that I want to file a bug on it...

When sending a file with a long name, the GUI expands in width - Not ideal!

---

### Post by ranf on 2006-06-11
Before you start it:
```
ps a > before
```

Then start it. Switch back to the terminal:
```
ps a > after
diff before after
```

Clean up:
```
rm before after
```

---

### Post by daller on 2006-06-13
I don't really get that...

What am I supposed to do?

---

### Post by ranf on 2006-06-16
The text in the [code] is supposed to be run in a terminal (Konsole? in KDE).

With "start it" I meant "Actions -> Send with bluetooth..."

---

### Post by daller on 2006-06-16
Oki, I get it...

"ps a" outputs the running processes...

And then it compares the before and after list...

...It was: kbtobexclient

Now I can send files to my cellphone easily.... thanks!

---


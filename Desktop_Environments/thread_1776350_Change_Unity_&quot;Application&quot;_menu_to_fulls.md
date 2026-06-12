---
title: "Change Unity &quot;Application&quot; menu to fullscreen. Possible?"
date: 2011-06-06
forum: Desktop Environments
---

### Post by snickasaurus on 2011-06-06
Currently using a 37" Visio as my main monitor I'd like to have the menu popout to fullscreen instead of just a quarter screen box. Is this possible? I've seen writeups on several configuration changers but non offer such an option. If there is one you know of or a setting I haven't found that's editable please point me in the right direction. Thanks in advance!

-snickasaurus

---

### Post by mc4man on 2011-06-06
How it will look you'll have to see - in a terminal

```
gsettings set com.canonical.Unity form-factor Netbook
```

To return - (Automatic can be replaced with Desktop - same thing in your case
```
gsettings set com.canonical.Unity form-factor Automatic
```

gsettings works on 
command (set), scheme (com.canonical.Unity), key (form-factor), value (Netbook)

---

### Post by snickasaurus on 2011-06-06
Didn't work...but it darn sure got me excited.  :-P
Thanks for your reply, I'll keep digging and post a solution if I find one.

---

### Post by mc4man on 2011-06-06
Works here on a 24" as far as default opening size - when you open any lens there should be a maximize button in bottom right corner - does that work?

---

### Post by snickasaurus on 2011-06-06
Indeed it does. Been using it but it's nice to not have to rely on my mouse when I don't have to. Know what I mean?

---

### Post by mcduck on 2011-06-06
If you have problems getting it working th the above commands, you could try installing the *dconf-tools*-package and then using the *dconf-editor* to change the key.

(in dconf-editor the relevant key shows as *desktop/unity/form-factor*, you can just click it and select the Netbook option from the list.)

---

### Post by snickasaurus on 2011-06-06
Thanks mcduck for the fix! And thank you mc4man for the help!

Issued solved!

---


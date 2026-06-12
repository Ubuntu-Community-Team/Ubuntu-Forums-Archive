---
title: "Disable Shift+Backspace"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Wr8EYilK8Y on 2006-06-30
I want to do this because its driving me nuts when I press them by mistake

---

### Post by invalid on 2006-06-30
[QUOTE=Your Name Is]I want to do this because its driving me nuts when I press them by mistake[/QUOTE]
```
xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"
```

---

### Post by Wr8EYilK8Y on 2006-06-30
Testing

EDIT: THANKS!!! Is that permanent?

---

### Post by invalid on 2006-07-01
[QUOTE=Your Name Is]Testing

EDIT: THANKS!!! Is that permanent?[/QUOTE]
Not permanent, you will need to add it to your start up script.

---

### Post by Wr8EYilK8Y on 2006-07-01
did so and tested it. Works now. Thanks. You saved me ^_^

---


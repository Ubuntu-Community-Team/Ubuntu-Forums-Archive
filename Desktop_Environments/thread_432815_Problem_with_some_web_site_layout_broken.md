---
title: "Problem with some web site layout broken"
date: 2007-05-04
forum: Desktop Environments
---

### Post by michelem09 on 2007-05-04
Hi,
I have an annoying problem with some web site layout page with Firefox and Epiphany.
This problem seems to be with Gecko applications and only from my own user.

If I switch in a different user (with a default/just created home) the problem disappear so I think this is something related to my user configuration only, but I dont know what I can do.
I tried to run firefox whit --safe-mode but the problem persists.
I attached you a screenshot for example.

---

### Post by ohgod on 2007-05-04
Are you allowing javascript in Firefox?

If it's just your account, then it could be a problem with your firefox configuration (but that wouldn't explain the epiphany problem...).

You could try moving your .mozilla file to a backup location so firefox will go back to the default settings:
```

mv ~/.mozilla ~/.mozilla_backup

```

Then if you want to go back to your settings you can move it back:
```

rm -r ~/.mozilla 
mv ~/.mozilla_backup ~/.mozilla

```

---

### Post by michelem09 on 2007-05-04
Thank you for the answer but unfortunately I tried your solution yet and it didnt solve the problem, I think it is a more general problem and not a firefox specific problem because it happens to Epiphany too, maybe something related to gnome/gconf? I dont know... :(

---


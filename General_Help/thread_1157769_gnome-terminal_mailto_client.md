---
title: "gnome-terminal mailto client"
date: 2009-05-13
forum: General Help
---

### Post by scarf on 2009-05-13
i am right-clicking on an e-mail address displayed in the gnome-terminal (for example, after the output of a whois query), and clicking "send mail to...", but i am getting this error:

```

Could not open the address “mailto:<email address>”:
Failed to execute child process "evolution" (No such file or directory)

```

that is because i uninstalled evolution, since i don't use it.  i use thunderbird, instead.

how can i tell gnome-terminal to use thunderbird?  thanks.

---

### Post by kanikilu on 2009-05-13
I don't think it's a setting in **gnome-terminal**. Is Thunderbird set as your default email client in System > Preferences > Preferred Applications (**gnome-default-applications-properties**)?

---

### Post by scarf on 2009-05-13
thank you! that was it!  evolution was still set as defualt mail client.  changing it to "Mozilla Thunderbird" now causes gnome-terminal to use thunderbird.

---


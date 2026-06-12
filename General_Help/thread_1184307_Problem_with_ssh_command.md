---
title: "Problem with ssh command"
date: 2009-06-11
forum: General Help
---

### Post by colau on 2009-06-11
```

ssh abc@abc-desktop
ssh: Could not resolve hostname abc-desktop: Name or service not known

```

---

### Post by trwww on 2009-06-11
Looks like you have a problem with DNS, not SSH.

---

### Post by maheshasolkar on 2009-06-11
If you know the IP address of 'abc-desktop' on your network, try using that first:

```
  ssh abc@192.168.0.102
```

or whatever the IP address of that machine is.

If that works, add that IP address to your /etc/hosts file and associate that with the name 'abc-desktop'. Somewhat like this in your /etc/hosts file:

```
  192.168.0.102    abc-desktop
```

Then try your original command again.

---

### Post by colau on 2009-06-11
> **maheshasolkar said:**
> If you know the IP address of 'abc-desktop' on your network, try using that first:

```
  ssh abc@192.168.0.102
```

or whatever the IP address of that machine is.

If that works, add that IP address to your /etc/hosts file and associate that with the name 'abc-desktop'. Somewhat like this in your /etc/hosts file:

```
  192.168.0.102    abc-desktop
```

Then try your original command again.
Thank you very much.It worked.:D

---


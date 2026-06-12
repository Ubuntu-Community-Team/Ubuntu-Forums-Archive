---
title: "authentication  window not working."
date: 2011-05-17
forum: Desktop Environments
---

### Post by rizos on 2011-05-17
right now i cannot use update manager, software centre or do any changes on users accounts because every time the authentication window while trying to type my password  shakes and disappear after 1 second.

making not possible to type my password.


if i use in terminal $ gksu software-center then i can use it no problems.

also synaptic works normally.

and my password as root still works.


i don't know what can be wrong, any ideas?


ubuntu maverick.

---

### Post by rizos on 2011-05-20
bump

---

### Post by Copper Bezel on 2011-05-20
Well, the first thing to check would be whether the problem is specific to your user settings or whether it's an actual software problem, I think. I'd create a new user account with admin privileges and try from there.

I think, actually, that the problem might be with Gnome's policy kit. Since I don't run it, I can't do any of the things you can't (edit users and groups or run softwarecenter without gksu.)

---

### Post by mmodi@argusoft.com on 2011-09-19
Is there any resolution to this issue. I am also having the same problem with Ubuntu 11.04 64 bit. Due to this issue I am not able to open the tool which requires authentication like Date-Time Change, Users-Admin, Synaptic Package Manager etc.

---

### Post by uncontrolable™ on 2011-09-19
Does it open with the following command?```
sudo synaptic
```

---

### Post by Krytarik on 2011-09-19
> **uncontrolable&#8482 said:**
> Does it open with the following command?```
sudo synaptic
```
Better refrain from running graphical apps with "sudo", use "gksudo" instead. For details, see here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

However, Synaptic actually shouldn't be affected by this issue.

---

### Post by uncontrolable™ on 2011-09-19
> **Krytarik said:**
> Better refrain from running graphical apps with "sudo", use "gksudo" instead. For details, see here:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

However, Synaptic actually shouldn't be affected by this issue.
Nice to know, thanks.

uncontrolable

---

### Post by Copper Bezel on 2011-09-19
mmodi mentioned Synaptic, though, which is where it gets weird, because Synaptic's .desktop launcher includes gksu, whereas the others call to the policy kit.

mmodi, Is it possible you've removed admin privileges from your account somehow? Does the authentication splash come up at all, or are you simply not prompted for a password?

---

### Post by mmodi@argusoft.com on 2011-09-19
> **Copper Bezel said:**
> mmodi mentioned Synaptic, though, which is where it gets weird, because Synaptic's .desktop launcher includes gksu, whereas the others call to the policy kit.

mmodi, Is it possible you've removed admin privileges from your account somehow? Does the authentication splash come up at all, or are you simply not prompted for a password?

Using sudo synaptic, I am able to open up Synaptic. Also I resolved issue related to Authentication window. It's something related to policy kit and resolved using following command.

sudo chmod +s /usr/lib/policykit-1/polkit-agent-helper-1

Thanks for your answers.

---

### Post by sisco311 on 2011-09-19
> **mmodi@argusoft.com said:**
> Using sudo synaptic, I am able to open up Synaptic. Also I resolved issue related to Authentication window. It's something related to policy kit and resolved using following command.

sudo chmod +s /usr/lib/policykit-1/polkit-agent-helper-1

Thanks for your answers.

polkit-agent-helper-1 must be [setuid root]("http://en.wikipedia.org/wiki/Setuid") and world-executable. chmod's +s option only sets the setuid bit on the file. To make sure that the ownership and all the permissions on the file are correct one could run:
```
sudo chown root:root /usr/lib/policykit-1/polkit-agent-helper-1
sudo chmod 4755 /usr/lib/policykit-1/polkit-agent-helper-1

```

More about Unix/Linux file permissions here: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---


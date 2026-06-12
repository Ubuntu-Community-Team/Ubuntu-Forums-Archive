---
title: "Retrieve List of Installed Programs to Install them on new computer"
date: 2009-03-01
forum: General Help
---

### Post by Jerrac on 2009-03-01
I just built a new computer. Stuck Ubuntu on it. Now I want to install all the programs I have installed on my laptop on my new desktop. What is a good way to do that?

I have tried listing all my programs with dpkg -l /* But it returns more than just the package name,, so I don't think it would be good just to paste that in.... Plus, I don't know what the uu and ii mean, I thought that command was supposed to only return installed programs, but the uu confuses me.

Also, should I worry about the fact that my laptop is 32bit and my new desktop is 64bit?

---

### Post by iaculallad on 2009-03-01
Create a list of all installed applications:

```
dpkg --get-selections > ~/packages
```

To restore the packages back:

```
sudo dpkg --set-selections < ~/packages && apt-get dselect-upgrade
```

HTH.

---

### Post by Jerrac on 2009-03-02
> **iaculallad said:**
> Create a list of all installed applications:

```
dpkg --get-selections > ~/packages
```

To restore the packages back:

```
sudo dpkg --set-selections < ~/packages && apt-get dselect-upgrade
```

HTH.

Thanks! It helped! The second code kept telling me that I didn't have permission to open dpkg/lock, even though I had closed all package managers, but I figured out how to get around it. :D

---


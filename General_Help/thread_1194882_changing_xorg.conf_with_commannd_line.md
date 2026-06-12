---
title: "changing xorg.conf with commannd line"
date: 2009-06-23
forum: General Help
---

### Post by Kimeras on 2009-06-23
I know how to edit xorg.conf as a user, but i want to add text to the end of the file as part of a shell script.

I've tried a few options such as:
```

echo "new line here" >> /etc/X11/xorg.conf

sed 's/$/new line here"/g' /etc/X11/xorg.conf
```

And the same commands as above with sudo but the changes don't save, i was thinking of copying a pre-made xorg.conf and replacing it but this is obviously not ideal.

Also i figure i will also run into problems automating this as any command with sudo will require the user to enter the password, is there a way to include the password into the script to keep it automatic?

---

### Post by Kimeras on 2009-06-23
With some help in IRC i've solved the problem to some degree

```
#!/bin/bash
sudo su
echo "Section "Module"
        Load    "dbe"
EndSection" >> /etc/X11/xorg.conf
exit
```

problem is that this code doesn't run from a script and i still have to manually enter the command

---

### Post by geirha on 2009-06-23
This should do it. Note that the tee command will both append the text to the file, and also print it to the terminal
```

sudo tee -a /etc/X11/xorg.conf << EOF
Section "Module"
        Load    "dbe"
EndSection
EOF

```

---

### Post by Kimeras on 2009-06-24
Brilliant, this works perfectly!
Thank you :)

---


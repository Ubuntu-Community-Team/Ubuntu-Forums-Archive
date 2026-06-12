---
title: "Skype not installing"
date: 2009-04-27
forum: General Help
---

### Post by Falx_ on 2009-04-27
I am attempting to install skype onto ubuntu 9.04.
When installing i simply get, 

"Could not open" 'skype-debian_2.0.0.72-1.i386.deb'

Yes i am new to ubuntu...
Thanks.

---

### Post by spiderbatdad on 2009-04-27
so you downloaded a deb package from skype.com, and when you click the package you get that error?
If that's the case...just a wild guess...are you the admin user of this computer? Perhaps the user account doesn't have permission.

---

### Post by maheshasolkar on 2009-04-27
I don't think your post has enough information.

How are you installing Skype? Did you download the .deb file from somewhere?

You can install Skype from the medibuntu repository, by doing the following:

```
  sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
  sudo install skype
```

For more information:

  [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Falx_ on 2009-04-27
Thanks for replying.
Yes i am admin.
I followed your code,
However i am getting "install: missing destination file operand after 'skype'

---

### Post by maheshasolkar on 2009-04-27
Argh.. that's my bad. The second command should be:

```
  sudo aptitude install skype
```

Sorry about that.

---

### Post by spcwingo on 2009-04-27
Edit:  I was too slow.

---

### Post by spiderbatdad on 2009-04-27
ok

---

### Post by Falx_ on 2009-04-28
Thanks, it worked.

---


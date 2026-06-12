---
title: "permissions in the home folder"
date: 2009-02-26
forum: General Help
---

### Post by theozzlives on 2009-02-26
My roomate is getting that error about the .drmc file at login and her permissions are set to 777, I went to the prompt and typed:```
sudo chmod 644 tina -R
``` then she couldn't login. So I changed it back to 777, went to the GUI and set permissions as follows:
owner--create and delete
group--access files
others--access files
She still gets that error at login but at least she can login, how do I fix the error.

---

### Post by sisco311 on 2009-02-26
[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by taurus on 2009-02-26
```
sudo chmod 644 /home/tina/.dmrc
```

---


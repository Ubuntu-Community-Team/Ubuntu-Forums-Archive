---
title: "Run script that needs root rights when a non-sudoer usere logs in."
date: 2009-01-10
forum: General Help
---

### Post by sztomi on 2009-01-10
Hi.

I have a small script, which I would like to run when a particular user signs in to ubuntu. However, there are some stuff in the script, that needs root permission, but the user is not in the sudoers group, and I do not want him to be in. Is it possible for him to run this script, and only this script with root rights (and preferably not being able to modify it)?

Thank you in advance.

---

### Post by caljohnsmith on 2009-01-10
You could give that user permission to just run that particular script as root by adding them to the /etc/sudoers file with something like:
```
<username> ALL = NOPASSWD: /path_to_script/script
```
Make sure to add that to the very end of the sudoers file so that none of the previous rules will supersede it, because the order of the rules in sudoers matters. Also, to modify your sudoers file, you would want to use "visudo" by doing something like:
```
EDITOR=nano sudo -E visudo
```
That will allow you to modify the sudoers file with the nano editor. How about trying that and let me know how it goes or if you run into problems.

---

### Post by sztomi on 2009-01-12
Hi,

It worked partially: when I executed the script with that user, the script did not work, however, when sudoing the script, it was OK, and did not prompt for the sudo password.

After all, I made a "starter" script, which contained:
```
sudo /home/username/theScript.sh
```

And it works perfectly.

Thank you very much for your help!

---


---
title: "How can I change  file permissions to subdirectories?"
date: 2008-12-24
forum: General Help
---

### Post by grs on 2008-12-24
What is the Linux command to change permissions on a directory and its subdirectories?
I want to give fule read/write/execute at the moment I am having to do it to each file individually which is taking forever.

---

### Post by bgerlich on 2008-12-24
sudo chmod -R 777 /directory_path/and_name

---

### Post by eBoxNet on 2008-12-24
chmod 777 *

this will set permissions to all files and folders in current working directory

i.e. if you are inside test folder will give full write and read permissions to all afiles and folders inside test folder ..

---

### Post by grs on 2008-12-24
> **eBoxNet said:**
> chmod 777 *

this will set permissions to all files and folders in current working directory

i.e. if you are inside test folder will give full write and read permissions to all afiles and folders inside test folder ..

The above command seems to give full permissions to the folder I'm in and the files and folder with in it, but no futher. How can I gett all sub-sub directories changed, if that makes sence?

---

### Post by bgerlich on 2008-12-24
As I said before

chmod -R 777 /directory_path/and_name

---

### Post by grs on 2008-12-24
That did it thanks.

---


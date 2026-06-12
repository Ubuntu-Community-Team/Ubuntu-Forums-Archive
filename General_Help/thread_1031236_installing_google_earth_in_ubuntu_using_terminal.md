---
title: "installing google earth in ubuntu using terminal"
date: 2009-01-05
forum: General Help
---

### Post by superpink99 on 2009-01-05
i want to install google earth in ubuntu using the terminal coz my firefox is having problems, can someone tell me the how to of it?

---

### Post by e_torano on 2009-01-05
Go to Terminal (Applications->Accessories->Terminal) and paste in the following command:

```
wget http://dl.google.com/earth/client/current/GoogleEarthLinux.bin && chmod +x GoogleEarthLinux.bin && ./GoogleEarthLinux.bin
```

Now just follow through the steps ;)

---

### Post by binbash on 2009-01-05
add medibuntu repos to your sources.list ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) then

sudo apt-get install googleearth-4.2

---

### Post by halovivek on 2009-01-05
hi 
i have installed google earth now and i am doing fine in 64bit. thanks for posting.

---

### Post by hawkhock on 2009-01-07
> **binbash said:**
> add medibuntu repos to your sources.list ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) then

sudo apt-get install googleearth-4.2


Hi -- Am having same problems as others with Google 4.3.  Uninstalled 4.3. Followed directions and added medibuntu repos to my sources list.  When I copied/pasted the sudo command from your post, terminal gave me E: could not find package googleearth-4.2.

Newbie - learning as I go -- can you help?

Georgi

---

### Post by hawkhock on 2009-01-07
IGNORE PREVIOUS POST - I did not do second step & get the GPG key installed. I've successfully installed googleearth-4,2.  Now to see if it works!
G


> **hawkhock said:**
> Hi -- Am having same problems as others with Google 4.3.  Uninstalled 4.3. Followed directions and added medibuntu repos to my sources list.  When I copied/pasted the sudo command from your post, terminal gave me E: could not find package googleearth-4.2.

Newbie - learning as I go -- can you help?

Georgi

---


---
title: "wget"
date: 2009-05-25
forum: General Help
---

### Post by m_adel on 2009-05-25
hi..
pllzz some one tell me more about these two lines, in details plzz

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
 

 sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list


```

---

### Post by colau on 2009-05-25
> **m_adel said:**
> hi..
pllzz some one tell me more about these two lines, in details plzz

```

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
 

 sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list


```
```

man wget

```
The first line for gpg key
```

man gpg

```

This will add this repository in /etc/apt/sources.list.d/medibuntu.list file
```

sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```

cat /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by mikewhatever on 2009-05-25
The first command fetches the authentication key for Medibuntu packages.

The second adds the Medibuntu repository to your sources.

---

### Post by m_adel on 2009-05-25
thnx for your reply ,but can u plz give me some details about 
authentication key

---


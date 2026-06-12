---
title: "apt locale problem?"
date: 2022-08-14
forum: Desktop Environments
---

### Post by nibal on 2022-08-14
Hi,

I just added a 2nd language in a fresh Kubuntu 20.04 install.
Now all console messages  from apt are in that 2nd language.
In my regional settings, I have specified that all formats and dates are to be in en_US.
How can i fix these apt console messages?


TIA
Nikos

---

### Post by &amp;KyT$0P# on 2022-08-14
Check which environment variables are language related -
```
env | grep -F LANG
```
Then you can try replacing your language with en_US in one or more of these environment variables, e.g.
```
LANG=en_US.UTF-8 sudo apt update
```
Does this do what you're looking for?

---

### Post by nibal on 2022-08-14
> **halogen2 said:**
> Check which environment variables are language related -
```
env | grep -F LANG
```
Then you can try replacing your language with en_US in one or more of these environment variables, e.g.
```
LANG=en_US.UTF-8 sudo apt update
```
Does this do what you're looking for?

Sorry, it didn't work:(

```
 -> env | grep LANG
LANGUAGE=en_US:el
LANG=en_US.UTF-8

-> LANGUAGE=en_US sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://security.ubuntu.com/ubuntu focal-security InRelease [114 kB] 
```

apt install still uses a mix of en_US and el:(

---

### Post by nibal on 2022-08-14
Thanks,

Actually you nailed the problem.
Just that your solution needed a bit tweaking.
If I place in my .bash_profile
export LANGUAGE=en_US
all apt messages are in en_US:)

---

### Post by nibal on 2022-08-14
Bug is in .config/plasma-localerc:

```
-> cat .config/plasma-localerc
[Formats]
LANG=en_US.UTF-8


[Translations]
LANGUAGE=en_US:el
```

Better fix that:)

---


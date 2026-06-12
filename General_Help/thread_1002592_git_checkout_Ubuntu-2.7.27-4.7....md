---
title: "git checkout Ubuntu-2.7.27-4.7..."
date: 2008-12-05
forum: General Help
---

### Post by adamlau on 2008-12-05
So I run the following after downloading a copy of the local repo:

```
git checkout Ubuntu-2.7.27-4.7
make menuconfig
```

But the kernel that is shown being configured is 2.6.27-rc7. Is 2.7.27-4.7 being displayed as 2.6.27-rc7 (am I configuring the proper kernel)? If not, how to checkout Ubuntu-2.7.27-4.7 out of my local repo to a seperate directory to build? I tried:

```
git checkout -b Ubuntu-2.7.27-4.7
```

...but did not notice the branch in **/home/user/ubuntu-intrepid/.git/branches**

Am I supposed to 

```
git commit -a
```

...after creating a branch in order to replicate Ubuntu-2.7.27-4.7 to **/home/user/ubuntu-intrepid/.git/branches** to build out of? Basically, how to checkout Ubuntu-2.7.27-4.7 out of my local repo to a seperate directory to build?

---


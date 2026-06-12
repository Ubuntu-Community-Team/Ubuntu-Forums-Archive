---
title: "ubuntu/Kubuntu boot screen"
date: 2009-10-22
forum: Desktop Environments
---

### Post by errors on 2009-10-22
Hi there i've installed kde on unbuntu and it changed my boot screen
i've try the "sudo update-alternatives --config usplash-artwork.so"
but it still hasn't change... :S it still loads using kubuntu screen.. :S
Can anyone help me?

---

### Post by Dullstar on 2009-10-22
I want to know that too - mine boots up with Ubuntu's, but then shuts down with Kubuntu's!  Why does it do that???

---

### Post by Zorael on 2009-10-24
> **errors said:**
> Hi there i've installed kde on unbuntu and it changed my boot screen
i've try the "sudo update-alternatives --config usplash-artwork.so"
but it still hasn't change... :S it still loads using kubuntu screen.. :S
Can anyone help me?
Did you do 'sudo update-initramfs -u -k all' afterwards?

> **Dullstar said:**
> I want to know that too - mine boots up with Ubuntu's, but then shuts down with Kubuntu's!  Why does it do that???
Perhaps your initramfs is set up with Ubuntu's but your alternatives symlink still point to Kubuntu's. Where does the **/etc/alternatives/usplash-artwork.so** symlink point to?

```
$ file /etc/alternatives/usplash-artwork.so
```
If it says **/usr/lib/usplash/usplash-theme-_kubuntu_.so**, then redo the update-alternatives and update-initramfs commands as above. If it says **-ubuntu**, that's curious.

---

### Post by errors on 2009-10-26
> **Zorael said:**
> Did you do 'sudo update-initramfs -u -k all' afterwards?



Nop, going to try that when i get home.

Strange.. now mine boot on with Kunbuntu screen a off with Ubuntu screen :P

---

### Post by JugglinPhil on 2009-10-26
You might be able to change it using Startup Manager, it is an easy way to change your usplash and it is availiable from the repos.

---

### Post by errors on 2009-10-28
kk! Problem solve after "sudo update-initramfs -u -k all" comand :D thx for the help ;)

---


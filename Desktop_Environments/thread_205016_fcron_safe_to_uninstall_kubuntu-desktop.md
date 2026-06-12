---
title: "fcron: safe to uninstall kubuntu-desktop?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by HippoMan on 2006-06-27
I'm using Dapper/Kubuntu.  I want to install **fcron**, but when I start to do so via aptitude, I'm told that **kubuntu-desktop** needs to be uninstalled along with **anacron**.  Is it safe to allow **fcron**'s installation to blow away the **kubuntu-desktop** package?

Thanks in advance.

---

### Post by hoodwink on 2006-06-27
Not really, or KDE will be gone. I can't help you, but you'll need to check the prerequisite package conficts thoroughly.

---

### Post by HippoMan on 2006-06-27
Well, I did check the prereq's.  Apparently,  **fcron** conflicts with **anacron**, which for some reason is a prerequisite for **kubuntu-desktop**.

I've used KDE all over the place (lots of linuxes), and I've never had any problem using **fcron** until now.

Can anyone suggest a way to get **fcron **working under kubuntu?

The only uninstalls that aptitude was demanding during the** fcron** install were these two: **anacron** and  **kubuntu-desktop** ... not any other KDE packages. Therefore, could it possibly be that **kubuntu-desktop** is a meta-package that in and of itself is safe to uninstall?  (I'm hoping!)

---

### Post by HippoMan on 2006-06-28
[quote=hoodwink]Not really, or KDE will be gone. I can't help you, but you'll need to check the prerequisite package conficts thoroughly.[/quote] In an unrelated thread, I found this: [http://www.ubuntuforums.org/showpost.php?p=1182373&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=1182373&postcount=4").

So apparently, it's OK to remove the **kubuntu-desktop** meta-package, after all.  I have now installed **fcron**, and this has caused **anacron** and **kbuntu-desktop** to be uninstalled, seemingly with no ill effects.

I'm keeping my fingers crossed.

---


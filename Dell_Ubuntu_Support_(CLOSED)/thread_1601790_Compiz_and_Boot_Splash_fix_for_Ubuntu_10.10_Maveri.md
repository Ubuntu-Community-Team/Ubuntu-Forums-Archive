---
title: "Compiz and Boot Splash fix for Ubuntu 10.10 Maverick Meerkat for Dell Mini 10v"
date: 2010-10-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fcn on 2010-10-20
I installed Ubuntu 10.10 using netbook cd iso and changed default  desktop to Gnome environment. Then I noticed I cannot change "Visual  Effects" settings and when opening a menu it flashes and things like  that. This happens  because compiz is not installed default. To install  it you can use Synaptic Package Manager from System -> Administration  menu or this command will install it:

```
sudo apt-get install compiz
```And at boottime, if you can't see splash screen during boot,

```
echo "FRAMEBUFFER=y" | sudo tee /etc/initramfs-tools/conf.d/splash
```will fix it I think.

I posted the same thread here too: [http://www.mydellmini.com/forum/ubuntu/23872-compiz-boot-splash-fix-ubuntu-10-10-maverick-meerkat.html#post172644](http://www.mydellmini.com/forum/ubuntu/23872-compiz-boot-splash-fix-ubuntu-10-10-maverick-meerkat.html#post172644)

---

### Post by m_zeid on 2010-11-05
hey man,

I have the same problem and your fix didn't work, it just made the purple color more bright !!

any other solutions ??

---


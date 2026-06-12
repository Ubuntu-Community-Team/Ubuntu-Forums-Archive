---
title: "Is kpackage broken?"
date: 2007-06-12
forum: Desktop Environments
---

### Post by FuturePilot on 2007-06-12
I installed Kubuntu Dapper and I also installed kpackage. So I tried to install a deb that I downloaded but it just gave me a bunch of dependency errors. And I had the option checked to check dependencies. Why won't it download and install the dependencies?

---

### Post by Anonii on 2007-06-13
It _checked_ for dependencies, didn't it? .debs, won't download and install the dependencies themselves, tho.
Why don't you try using APT? From what I see kpackage is available in the universe, so Synaptic should have it.
[http://packages.ubuntu.com/dapper/admin/kpackage](http://packages.ubuntu.com/dapper/admin/kpackage)

---

### Post by FuturePilot on 2007-06-15
I don't think it did. It just started the command dpkg -i xxxxx.deb then gave a bunch of errors due to missing dependencies. I know if you use Gdebi and there's missing dependencies it will automatically download them.

---

### Post by Anonii on 2007-06-16
> **FuturePilot said:**
> I don't think it did. It just started the command dpkg -i xxxxx.deb then gave a bunch of errors due to missing dependencies. I know if you use Gdebi and there's missing dependencies it will automatically download them.
Why don't you try using APT? From what I see kpackage is available in the universe, so Synaptic should have it.
[http://packages.ubuntu.com/dapper/admin/kpackage](http://packages.ubuntu.com/dapper/admin/kpackage)

---

### Post by FuturePilot on 2007-06-17
Sorry if I didn't explain this better. Here's the situation. I have kpackage already installed. I was trying to install Envy which depends on a bunch of development packages. So I try to install Envy with kpackage. But it doesn't download the dependencies and just gives errors because of the missing dependencies. I know in Gnome if you install anything with Gdebi it will download and install all of the dependencies. Maybe kpackage doesn't work the same way?

---


---
title: "Update Has Broken My X/Nvidia Setup"
date: 2012-09-25
forum: Desktop Environments
---

### Post by nshiell on 2012-09-25
Hi
I had an error when I booted my PC telling me that an update had failed and that I should run a partial update to fix the issue.

I rand the update

After I rebooted I found my Proprietary Nvidia drivers weren't installed. I need graphics drivers for dual head and other 3D stuff.

I have tried everything I can think of, reinstalling the drivers, downloading the drivers from NVidia's website, reinstalling x, nothing I have tried seems to work.

I need some advice on how to get things working again, maybe downgrading stuff?
What would help you to give me help? Log files? error messages? hardware / software versions?

Many thanks

NShiell

---

### Post by cogier on 2012-09-25
Open terminal by pressing **[Ctrl]+[Alt]+T** 

Enter
```
sudo apt-get install -f
```

Then
```
sudo apt-get update
```

Then
```
sudo apt-get upgrade
```

That may help.

---


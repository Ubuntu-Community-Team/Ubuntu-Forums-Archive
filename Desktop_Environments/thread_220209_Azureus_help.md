---
title: "Azureus help"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Amorphous_Snake on 2006-07-21
I have some questions regarding Azureus:

1- I installed it through Automatix, but it installed the latest beta. I don't like to work with betas, when there is a full version available. How can I return to the latest stable version?

2- There are updates for the plugins in Azureus. When I download them, I get an installation error saying that /opt is not writable. What shall i do?

---

### Post by sabredog on 2006-07-21
> **Amorphous_Snake said:**
> I have some questions regarding Azureus:

1- I installed it through Automatix, but it installed the latest beta. I don't like to work with betas, when there is a full version available. How can I return to the latest stable version?

2- There are updates for the plugins in Azureus. When I download them, I get an installation error saying that /opt is not writable. What shall i do?

You will need to go to terminal

```
sudo /opt/azureus/azureus
```

and install the plugins from there, once Azureus loads. Automatix installs a system wide version of Azureus which means you need to be super-user to install updates and plugins.

[http://ubuntuforums.org/showthread.php?t=144546&highlight=howto+azureus](http://ubuntuforums.org/showthread.php?t=144546&highlight=howto+azureus)

Try the above link for the best way to install Azureus outside of using Automatix.

Hope that helps!

---


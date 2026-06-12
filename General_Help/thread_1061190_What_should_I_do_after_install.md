---
title: "What should I do after install?"
date: 2009-02-05
forum: General Help
---

### Post by Bozmeister on 2009-02-05
Greetings from the UK.

Hello, I have just installed VirtualBox on my laptop and installed Ubuntu 8. When I click on Devices - Install Guest Additions, Nothing happens? I input this command:

sudo apt-get install dkms Ubuntu updated files and then stopped. Has anyone got any advice on where to go to get me up and running?

I had a crazy idea to start PHP programming using Mysql on Apache server all running on Ubuntu on my VirtualBox . I guessed the open source route (LAMP) is the way to go. I have knowledge of classic ASP using IIS. This Ubuntu is something else. Command prompts are scaring me. ;0  I think Apache is already installed.

Hope you can help?

I have my Ubuntu Noob hat on!

---

### Post by beno1990 on 2009-02-05
If I read that right, the guest OS is Ubuntu?

If that's so, then in the guest OS (Ubuntu) type the following into the terminal to install the guest additions from the Ubuntu repositories instead:

```
sudo apt-get install virtualbox-ose-guest-utils
```

---


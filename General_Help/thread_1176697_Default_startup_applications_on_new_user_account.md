---
title: "Default startup applications on new user account"
date: 2009-06-02
forum: General Help
---

### Post by Ingenium on 2009-06-02
How can I change the set of default startup applications on a new user account? Once the account is created, it's easy to go into System > Preferences > Startup Applications to change them, but there has to be a way to change what they are by default.

The problem mainly stems from using the Guest session feature. It doesn't remember the settings for startup applications. So every time I switch to it, it loads up a lot of programs I have for my account that I don't want running for the guest account (such as Google Desktop).

---

### Post by mcduck on 2009-06-02
Everything inside /etc/skel will be copied to new user's home directories..

Create a new user, configure the settings the way you'd like the desktop for guest user to be like, and then copy all the configuration files from that user's home to /etc/skel. You can remove that extra user afterwards.

---


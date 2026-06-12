---
title: "RDP Kiosk?"
date: 2009-05-20
forum: General Help
---

### Post by Beltaine on 2009-05-20
Done a fair bit of searching and haven't found any solutions yet, so thought I'd see if someone can point me in the right direction.

I work for a public school system and this year we moved all of our lab computers to a Terminal services client setup.

We have a pair of Windows 2003 Terminal Servers that are set up to provide lab computers with a locked down desktop.

the clients themselves are running Windows XP Pro, locked down with Microsoft SteadyState. When the systems boot, they automatically log into the local student account which can do nothing except run the Microsoft Remote Desktop Client. It's called in a startup batch file so it connects automatically to the account associated with the location of the lab. Once a user logs out of the RDP session, the local workstation also logs out so that the user does not have access to the local desktop.

Due to licensing issues, we'd like to set up some flavor of Linux to do the same thing as our XP machines.

We need the following:

1. Users can do nothing to the local machine other than turn it on/off.
2. When the machine is turned on, it automatically logs in as the local linux user, connects to our Terminal Server via RDP which is presented full screen and seamless.
3. Audio from the Terminal Server needs to play on the local machine.
4. Users need to be able to save to USB drives connected to the local machine.
5. Once logged out of the Terminal Server, the local machine needs to log off, restart, or otherwise restrict the user from doing anything other than starting the RDP connection again.

The OS will be loaded on the machine's local hard drive.

Any help in pointing me in the right direction would be great.

---

### Post by Beltaine on 2009-05-20
Can I do this with LTSP but have the clients point to my 2003 Terminal server instead?

---


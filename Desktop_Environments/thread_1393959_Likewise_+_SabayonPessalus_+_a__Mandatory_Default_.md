---
title: "Likewise + Sabayon/Pessalus + a  Mandatory Default Desktop Profile?"
date: 2010-01-30
forum: Desktop Environments
---

### Post by web1b on 2010-01-30
We would like to setup a pool of Linux (I assume Ubuntu is best) laptops for employees to borrow and take home for the purpose of only using VPN and Terminal Services Client and Firefox.  They will do the real work via Remote Desktop and the laptop will be only used as a remote control terminal.  The purpose of the browser is just so they can verify internet connectivity before lauching VPN as well as to log into WIFI hotspots that require web login.

We need the users to be able to log in to these laptops with their Active Directory domain user accounts and arrive to a preconfigured desktop with VPN client already configured with VPN host name (they must enter their own VPN user name and password each time).
Firefox should be installed with a mandatory home page.  They should not have ability to download or save anything from Firefox.
A mandatory desktop wallpaper must be set for all domain users.

The desktop needs shortcuts to Firefox, Terminal Services Client and the configured VPN client so they don't need to go digging in the menus to find them.
All the menus needs to be disabled and locked out so all the users can do is log in, run those applications, log out and shut down the computer.  They should not have any ability to save any files to the computer, not even be able to save a text file to their own desktop.

I have figured out how to join a machine to a domain with Likewise and I have heard that Sabayon can lock down the desktop, but I don't know how to make a model profile that all domain users will get when they log in so everyone has the same mandatory set up.

---


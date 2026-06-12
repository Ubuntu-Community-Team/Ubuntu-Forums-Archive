---
title: "Removing KDE secrets on wifi reconnect"
date: 2010-11-18
forum: Desktop Environments
---

### Post by IFailAtLinux on 2010-11-18
I installed Kubuntu on my PC I want to use remotely, without having keyboard, mouse nor monitor connected to it. So I want it to reconnect automatically if it loses the connection.

I upgraded to newest version of kubuntu, so I have KDE4 and newest network manager app. I have password set to my KDE wallet, so I enter it on boot and the app connects.

But then if kubuntu loses connection and tries to recconect a window appears with "secrets", where I have network connection screen, the password for my wireless network is already in the necessary field and all I have to do is press OK.

Well, I don't want that window to appear. The app already remembers my password, it detects it has to reconnect, but it makes me confirm the password is correct? I want to make it just connect, without my input. But I have no idea where to look. 

I've checked the options in network manager, but nothing on that. Then I don't want to change the app if I won't have to, linux tends to be pretty touchy with my network card and I'm afraid it could stop detecting it or something...

Edit: The window appeared again so now I can put full title of it: "Secrets for [NetworkName] - KDE Daemon". Under it I can choose security type for [NetworkName], there is field for password, with the password already inserted and "show password" field under it. Oh, and OK button.

Edit 2: Obviously KDE wallet has "always allow" option for KNetworkManager.

---

### Post by IFailAtLinux on 2010-11-25
Ok, I've turned off KDE wallet. KNetworkManager still uses that stupid pop-up when it loses WiFi signal.

So I'm changing my question: I'm looking for network manager that will:
1) detect WiFi access points and will work with my hardware(MSI PC54G3). I have experience with network managers not working with this card
2) can remember network passwords
3) will try to reconnect when it loses connection without asking me anything. And it will try again and again until it succeeeds.
4) I'm not scared of command line nor I'm afraid of editing config files, but GUIs are good.

If not the fact I already had experience in which bad network manager did work with my card, then I installed another that didn't work, then I went back to the bad one and it didn't work anymore I would just check them all myself. But I've already installed a lot of stuff on that computer and reinstalling it if I mess up internet will take a week or so. If I ever get it running again, hahah, I fail at linux.

---


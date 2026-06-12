---
title: "Anyone Get WICD to work with a Dell Studio 15n?"
date: 2009-07-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlacroix on 2009-07-26
I am using Kubuntu 9.04 on my Dell Studio 15n. Kubuntu's default network manager is broken, so I usually use Wicd instead. With my other laptop this works fine. With my Dell Studio it will work wonderfully the first time for about ten minutes, and then it will never work again until I uninstall and reinstall it. (Essentially, I have to reinstall it, reboot, get 10 minutes of use, then repeat). It hangs at obtaining IP address.

I am using the default Kubuntu network manager plasmoid right now, but that's frustrating me too because it shows an "unplugged" icon even though it is connected so I cannot tell if it is connected or not by looking at the icon.

Has anyone had success with wicd on their Studio or know what my problem might be?

---

### Post by rubaiyati on 2009-07-26
wcid, just works fyn with me.

b4 installing wcid, did u completely remove the network manager???
If not, try to remove it n then install wcid.

---

### Post by jlacroix on 2009-07-26
Still doesn't work. I did:

sudo apt-get remove --purge plasma-widget-network-manager network-manager wicd && sudo apt-get install wicd

Then I rebooted. When it came up I entered all of my details and the connection came up in about 5 seconds. I was able to use the internet for about 5 minutes. Then, it dropped connection and no amount of reconnecting or rebooting will get it back.

---


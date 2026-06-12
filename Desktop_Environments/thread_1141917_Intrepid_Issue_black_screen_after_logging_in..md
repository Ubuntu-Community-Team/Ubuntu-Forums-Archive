---
title: "Intrepid Issue: black screen after logging in."
date: 2009-04-28
forum: Desktop Environments
---

### Post by Omicron Machine on 2009-04-28
The machine is a recent HP laptop. This began to occur right after the last time it was updated. It said there was an updated nvidia driver--180 instead of 170--and after activating it, I rebooted. The login screen comes up and is 100% normal. But if I log in to Gnome, even failsafe Gnome, the screen shows a cursor for a moment, then that disappears and it just sits there with a black screen. Not even blank, just black, as if the laptop were powered off.

I am able to login, but only to a failsafe terminal. From that terminal, all my applications still work as normal. If I go, for example, sudo firefox, then Firefox comes up, with the skin in place and working and the metric ton of add-ons all functioning and in place. Or, at least, functioning as far as they can without internet, possible because it's in failsafe, and possibly because it's not detecting USB ports at all and I use a USB key for internet because of an unresolved (and unrelated) wireless problem.

The applications all work, but the most interesting thing (from my limited point of veiw, anyways) is that trying sudo compiz recreates the error as if I'd tried to login to Gnome normally from the top. 

I suspect this is a matter of setting it back to the old driver, but I don't know how to do that from terminal. On the other hand, I may be totally off base. Any assistance would be appreciated.

Thanks much for reading and have a great day, everyone! :)

---

### Post by andrea000 on 2009-04-28
If it is just a driver problem and you can sudo Firefox 
and it launched then sudo synaptic in terminal nvidia
drivers should be in synaptic.Don't forget to uninstall
the driver your using just uncheck the one your using
and check the one you would like to install then click
apply.When done restart. 

sudo synaptic

best of luck

---

### Post by Omicron Machine on 2009-04-29
Thanks! I'm going to try that as soon as I get back from this library. Given I was using the 170 driver previously, will I still be able to re-install that one with Synaptic even though the laptop can't get on the internet untill this is fixed?

---


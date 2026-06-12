---
title: "My Ubuntu has mind of it's own!!- Internet problem"
date: 2009-04-13
forum: General Help
---

### Post by jack_harper2007 on 2009-04-13
Hi everyone!! I'm having a this problem:

I have my internet connection activated and i can get to some sites but i can't access others sites, for example i can go to google, [www.getdeb.net](www.getdeb.net) but i can't go to hi5.com, also i can enter other sites like yahoo, hotmail and even Ubuntu Forums but the browser that i'm using freezes when i try to login. And theres even other sites like youtube where i can at one time enter and the next time i can't. Also i can't login with a IM i tried pidgin and emesene. (I think that my OS is trying to disconnect me from the outside world, i guess it doesn't approve my friends xD)

While trying to solve this problem i:
1. Tried access the sites using Firefox and Epiphany, the problem was the same in both browsers
2. Clear all the cookies in both browers, it didn't work
3. Clear the cache using Ubuntu Tweak, it still didn't work
4. Check the connections between the modem and the computer, still the same, it didn't work
5. Reebot the computer did everything from step 4 to step 1 and it still didn't work

I don't think the problem it's in the modem because i have it for about a month and it didn't give me any problems (so far at least)

I don't see any reason why this is happening it looks like i can't go to some sites just because my Ubuntu doesn't feel like going there, perhaps its not in the mood for videos or checking e-mails right now xD

Can someone help-me solve this? Thanks!!

---

### Post by Therion on 2009-04-13
What do you mean you "can't go there"?  What happens exactly?

---

### Post by antikristian on 2009-04-13
I suspect you have a network issue

try to visit secure sites like [https://mail.google.com/](https://mail.google.com/)
If that does not work then run a ping -s 1400 [www.google.com](www.google.com) and se if you lose packets

---

### Post by jack_harper2007 on 2009-04-13
> **Therion said:**
> What do you mean you "can't go there"?  What happens exactly?

The browser freezes or the page turns white and keeps loading but nothing appears.

---

### Post by Therion on 2009-04-13
And you have Flash and Java and such installed, correct?

If not:```
sudo apt-get install ubuntu-restricted-extras
```
Enter your password and follow the prompts.

---

### Post by jack_harper2007 on 2009-04-13
> **Therion said:**
> And you have Flash and Java and such installed, correct?

If not:```
sudo apt-get install ubuntu-restricted-extras
```
Enter your password and follow the prompts.

I already have Java and Flash installed

---

### Post by antikristian on 2009-04-13
Do you have other computers or operatingsystems to test with?

---

### Post by jack_harper2007 on 2009-04-14
> **antikristian said:**
> Do you have other computers or operatingsystems to test with?

No i only have Ubuntu 8.10 installed

---

### Post by antikristian on 2009-04-14
as i tried asking earlier, do you get this problem mainly when you try to access or log into secure sites? sites with https:// in front of them?

---

### Post by Eredeath on 2009-04-14
Where do you live? Are you in a place that the ISP might be banning sites?

---


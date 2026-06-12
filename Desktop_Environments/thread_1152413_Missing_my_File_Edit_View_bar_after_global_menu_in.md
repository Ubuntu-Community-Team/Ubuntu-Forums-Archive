---
title: "Missing my File Edit View bar after global menu install"
date: 2009-05-07
forum: Desktop Environments
---

### Post by yahntzeid on 2009-05-07
I have searched all over for a solution to my problem most likely stemming from me dabbling with the global menu applet.  I had added it to my top panel and then didn't like it so i removed it.  However now I don't have the File Edit View menu bar on the top of my other applications.

I have removed the global menu as per numerous threads here that solved others who had similar issues but to no success for me.

Any solutions would be greatly appreciated.

---

### Post by floborg on 2009-05-07
Did you uncheck the enable box under Preferences prior to removing it from the panel?

---

### Post by yahntzeid on 2009-05-07
No i do not believe I did

---

### Post by floborg on 2009-05-07
Add that sucker back to the panel, uncheck enable, and remove it from the panel.  See what happenes.

---

### Post by aphelionos on 2009-06-02
Thanks. I had exactly the same problem in Jaunty 9.04. This solved it for me.

Global menu is an unstable and unnessecary applet in my oppinion.

---

### Post by nearlyrandom on 2009-06-26
Hopefully this is helpful for you.  I had the same problem with the menu bar disappearing.  I was able to fix it by opening nautilus with:

gksu nautilus

you are prompted for your password, the window opens
Then select the -->view -->reset to defaults within the nautilus window.

I then closed the nautilus window, and opened some of the programs that were previously missing the menu bar (transmission in my case) and they have been restored.

Hope that this works for you.

---

### Post by Enlightened Shadow on 2009-12-16
> **floborg said:**
> Add that sucker back to the panel, uncheck enable, and remove it from the panel.  See what happenes.

LOL thanks so much. This really helped me. It's crazy how something so small and over looked can cause such a fuss.

---


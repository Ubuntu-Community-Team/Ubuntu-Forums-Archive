---
title: "Update Alert in User Account"
date: 2009-04-08
forum: General Help
---

### Post by GMarkow on 2009-04-08
Hi All,
  Is there a way to get the update manager to check for updates and alert me of updates from my user account the way it does in my administrator account?

To put it  another way, when there are important updates how do I get Ubuntu to but that little red arrow in one of my panels when I'm not logged in as the administrator. 
Thanks,
Greg

---

### Post by Lunx on 2009-04-08
> **GMarkow said:**
> Hi All,
  Is there a way to get the update manager to check for updates and alert me of updates from my user account the way it does in my administrator account?

To put it  another way, when there are important updates how do I get Ubuntu to but that little red arrow in one of my panels when I'm not logged in as the administrator. 
Thanks,
Greg

Not sure I quite understand what you mean. When you log in normally you are logging in as a user, not as administrator (more correctly "root"). When updates are available the icon should appear on its own accord AFAIK. You could always simply go to System --> Administration --> Update Manager (That's in Jaunty, can't recall if it's called Update Manager in Intrepid or early releases). When you try to update it asks you for your password and this actually lets you temporarily borrow root powers to make the changes (it's letting you "change" from user to admin)

---

### Post by Lunx on 2009-04-08
What I was trying to say (badly I think) is that there is never any need to run as "Administrator" or root, **sudo** was created for this very reason, as it makes it very difficult to do things which may have drastic consequences and disastrous results.

---

### Post by GMarkow on 2009-04-08
Let me clarify a little bit. I think my terminology was wrong and therefore confusing, sorry.


When I installed Intrepid the first account I used was called 'meadmin'. With this account I make all my administrative changes to the system. From there I created several other accounts, 'me', 'guest' etc. 

Now, meadmin is the only account that can perform administrative duties in Gnome or in the terminal. For example if I want to run chmod from the terminal in the me account I need to first change user, i.e. 'su meadmin' and then run chmod. 

Now I rarely log into meadmin because I rarely need to make administrative changes. Except for updates. So when I log into the account I use most, 'me', it doesn't alert me to new updates. 

That's what I'd like to change. I want my 'me' account to display that little arrow that lets me know updates are available without having to login to my meadmin and without having to manually run the update manager.

Thanks again,
Greg

---


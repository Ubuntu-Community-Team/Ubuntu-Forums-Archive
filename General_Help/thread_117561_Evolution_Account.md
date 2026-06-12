---
title: "Evolution Account"
date: 2006-01-15
forum: General Help
---

### Post by titop33 on 2006-01-15
I used evolution for several years.
I first noticed that emails passwords cannot be deleted or changed :
You have to erase the file .gnome2_private/Evolution to erase passwords.

Today, I tried SMTP encryption, with my webhost smtp server.
It uses a self-signed certificate.
It did not work.
But after, removing SSL encrption from the configuration, I still cannot send email, as when sending email, I got a message telling that the certificate is corrupted.
The problem is : I don't use encryption anymore.
So I tried to remove the .gnome2_private/Evolution, the complete .evolution directory, reinstall evolution, but nothing changed.
So the question is : what can I do to be able to send email again?
Where does information about email senders are stored on my disk?
Thanks
Christophe

---

### Post by rajeshgautam on 2007-03-08
I am sorry I dont have a solution. But you have provided me with the solution for a problem of mine. I was searching the forums for a complete day to find a solution to my problem.

I am using evolution 2.8.1 in the edgy eft. I added POP accounts, but was unable to change the passwords after setting them once. Unchecking the "remember password" in the "receiving email" option was of no use. Evolution won't prompt for the password.  Deleting the account and creating it again had no effect.

The evolution password are stored in the  .gnome2_private/Evolution . You will have to delete/edit this file to permanentaly delete the account's password.

Hope you find the solution to your prpblem soon.

---


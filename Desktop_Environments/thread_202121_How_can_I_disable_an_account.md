---
title: "How can I disable an account?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by stychman on 2006-06-22
I've searched all through the User and Groups program in the Administrative menu but can't find how to disable an account.  
What I'd like to do is temporarily disable an account so the account is not usable for now but can be enable later on.   I don't mind doing some command line if that is necessary.

---

### Post by aysiu on 2006-06-22
I think you can just delete the account without deleting the user's /home directory. I'm not 100% sure if the re-created user would then be able to use that same /home directory, though.

---

### Post by scxtt on 2006-06-22
are you trying to stop someone from using an account on your box? -- if so, just change the password or maybe remove the entry for the default shell ...

what are you doing this for?

---

### Post by stychman on 2006-06-23
I'd like to just be able to disable the account so when I need to enable it again I don't have to go through and create all the permissions again.  If I create a specific group and then add it to that group when I make the account again it would be simpler.  In Windows you can just disable an account by checking off a box.  I think this should be an option in Ubuntu too.

---

### Post by Ramses de Norre on 2006-06-23
```
sudo gedit /etc/shadow
```
And set the entry after the username to *, like it is done with root when you didn't change anything.
Example: ```
root:*****:13187:0:99999:7:::

```
The user will have a random password then so he can't log in, to re-enable the user do sudo passwd user_name to set a normal password again.

---


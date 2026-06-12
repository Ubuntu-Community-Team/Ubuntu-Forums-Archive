---
title: "Changing password and keyrings"
date: 2009-05-14
forum: General Help
---

### Post by RJ12 on 2009-05-14
So I just recently changed my password using users and groups. But now when I log in there is a message that says: NetworkManager wants to access the keyring and asks me to input a password which I have to use the my old password. Do I have to change the password back? Or did I change it wrong or how do I get it to automatically connect without using my old password?:???: 

P.S. I didnt know how to mark as resolved so I changed the title

---

### Post by BslBryan on 2009-05-14
Hello, RJ12. :-)

The reason this happened is because when you set up your first user account, right after the Ubuntu setup, your password is also set up as root's password.  

To change root's password to what your new password is, open up your favorite shell and run a 
```
sudo passwd
```

You'll be prompted to type the new password in twice after that.

I hope I've been of some help. 

Best to you, and good luck. :-)

---

### Post by RJ12 on 2009-05-14
> **BslBryan said:**
> Hello, RJ12. :-)

The reason this happened is because when you set up your first user account, right after the Ubuntu setup, your password is also set up as root's password.  

To change root's password to what your new password is, open up your favorite shell and run a 
```
sudo passwd
```

You'll be prompted to type the new password in twice after that.

I hope I've been of some help. 

Best to you, and good luck. :-)

OMG Thank you I will use this everytime I change my password

---

### Post by RJ12 on 2009-05-16
*Bump*

---


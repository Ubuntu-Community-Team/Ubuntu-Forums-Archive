---
title: "How to Create New Users"
date: 2009-03-24
forum: General Help
---

### Post by mdgrech on 2009-03-24
I want to add a new admin users with default settings.  I tried doing it thru system>admin>users and groups when I logged in the users had the same applications already installed as my other admin account.  I want the new admin user to have same settings that Ubuntu comes with out of the box, please help.

---

### Post by Lunx on 2009-03-24
Having a read through chapter 5 of the pocket user guide may be useful

[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

---

### Post by mdgrech on 2009-03-24
Looked at the PDF, didn't answer my question though :(

---

### Post by mocoloco on 2009-03-24
You say the new admin user has access to the same apps as your other admin user. Isn't that what you want, or did you mistype something?

If you open "Users and Groups", unlock it, and view the preferences for your user, an "admin" should have everything checked under the "User Privileges" tab.

---

### Post by ibuclaw on 2009-03-24
> **mdgrech said:**
> I want to add a new admin users with default settings.
All new users are created using the default settings at the time of creation. As found in **/etc/skel**.

> **mdgrech said:**
> when I logged in the users had the same applications already installed as my other admin account.
Why does this seem odd to you? If you install an application, it is available for all users. Why would it be any other way? What are you exactly asking?

> **mdgrech said:**
> I want the new admin user to have same settings that Ubuntu comes with out of the box, please help.
Have you editted any settings in /etc ? No? Then they are more than likely to have the same settings that Ubuntu comes with out-of-the-box. There is nothing wrong with the way you created the users.

If you don't want certain menu elements available to them, then remove them (Right-Click -> **Edit Menus**).

Regards
Iain

---


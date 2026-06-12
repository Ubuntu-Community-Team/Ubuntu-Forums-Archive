---
title: "Sudousers with a Windows Active Directory"
date: 2009-03-26
forum: General Help
---

### Post by wydileie on 2009-03-26
I have an Active Directory set up that delivers some group names and numbers to my Linux users on the domain. Every now and then the group names are not properly delivered to the users, but the group numbers are always there. Using visudo I give users the ability to sudo, but it does not work with the name sometimes, as it is not properly delivered. So, I tried to use the group number instead since it is always available. Yet, the number does not work in the place of the name and I have tried all different combos to try to get it to work. Essentially my code is:
```
%<group_name> ALL=(ALL) ALL
```

and I need it to be something like

```
%<group_number> ALL=(ALL) ALL
```

If anyone knows the code to use the group number instead of name, that would be extremely helpful. I tried searching on the internet and forums all over the place, but did not see any examples of using group numbers instead of names.

---


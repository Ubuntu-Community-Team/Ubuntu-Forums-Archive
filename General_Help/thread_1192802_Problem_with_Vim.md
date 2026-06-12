---
title: "Problem with Vim"
date: 2009-06-20
forum: General Help
---

### Post by LakatosI on 2009-06-20
So yeah. I'm pretty new to Ubuntu, recently installed Intrepid Ibex, and I was fooling around, and now when I'm trying to learn to use Vim for programming for some reason it says it's unable to access, well, almost every vital file: like the .vimrc, or even the help files. Using sudo apparently fixes the problem, but still, it's very annoying to type in sudo every single time before using it. Any help?

---

### Post by synapsys on 2009-06-20
Sounds like you changed the permissions for the file folder where vim is contained. Maybe when you were 'fooling around.' I would suggest hunting down all the files/folder and making sure they have the appropriate permissions or re-install vim.

---

### Post by Bachstelze on 2009-06-20
It's normal.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by LakatosI on 2009-06-21
I tried reinstalling it, th file permission is ok on that folder, but still, It won't work.

---

### Post by paperplate9 on 2009-06-21
ls -l folder_name_here

(that's a small "L")

---

### Post by LakatosI on 2009-06-29
Please people. I'm getting desperate. I really like VIM, but using it like this, having to type sudo each and every time I try to run it is crazy. Can anybody help me?

---


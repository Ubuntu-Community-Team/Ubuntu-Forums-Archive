---
title: "No text rendering in Firefox or Epiphany"
date: 2009-06-03
forum: General Help
---

### Post by ntbutler on 2009-06-03
Hi all.

I am having a little problem with my internet. I have been using Firefox, but once I upgraded to 9.04, I have noticed that all text in Firefox is not being rendered.

I have also tried Epiphany with the same result.

At the moment I am using Opera, which seems to be working normally.

Does anyone have any ideas as to what is going on?

Thanks

---

### Post by ntbutler on 2009-06-05
bump

---

### Post by omisaza on 2009-06-06
Hello, I had same problem, I think,  try many things,  the Ubuntu appearance (compiz off) , I thought was problem with gecko engine, I try changing fonts on firefox preferences , finally I solved the problem changing the permissions to the fonts in /usr/share/fonts/truetype/msttcorefonts  ,  opening the folder as root: terminal: sudo nautilus , and folder (msttcorefonts) properties > permisions > changed all file access to read and write and Apply Permissions to Enclosed files, it worked , is safe? , i hope so.

[IMG]http://launchpadlibrarian.net/14757933/Pantallazo-Google%20-%20Mozilla%20Firefox%203%20Beta%205.png[/IMG]

---

### Post by negotiation on 2009-07-09
[SIZE=3]Thanks Omisaza,

Tried your method - using both: 'sudo nautilus' - the permissions didn't change.
Then tried following command: [/SIZE]
[SIZE=3][COLOR=#000000]sudo chmod 777 /usr/share/fonts/truetype/msttcorefonts

Same thing, permissions didn't change. 
[/COLOR][/SIZE]

---

### Post by negotiation on 2009-07-09
Here's the command:
[SIZE=3][COLOR=#000000]sudo chmod -R 777 /usr/share/fonts/truetype[/COLOR][/SIZE]

---


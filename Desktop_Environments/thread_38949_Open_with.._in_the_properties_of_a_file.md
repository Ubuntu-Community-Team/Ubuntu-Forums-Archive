---
title: "Open with.. in the properties of a file"
date: 2005-06-02
forum: Desktop Environments
---

### Post by gdcondor on 2005-06-02
Hi 

when I want to add an application in the "open with..." menu of a file (by adding this application in the "open with..." part in the properties) I always have the following error :
"Could not add application to the application database"

What's that ? :(

Thanks for your help !

---

### Post by mcclane on 2005-06-03
~/.local is owned by root so you have to a) make yourself/your group the owner. b) Change permissions to suit you. 

I don't know if this is the "proper" fix or not but it works. 

sudo chown -R 'USERNAME':'GROUP-ID .local
sudo chmod -R 700 .local

I had the same problem. This should fix it.

---

### Post by statsministern on 2005-06-03
Hmm that didnt help me cause i'm the owner of .local... even tried sudo chown -R 'USERNAME':'GROUP-ID .local
sudo chmod -R 700 .local but that doesnt do anything  ;-) 

Well I want to ad open with vlc for gtk but other players work fine to ad...

---


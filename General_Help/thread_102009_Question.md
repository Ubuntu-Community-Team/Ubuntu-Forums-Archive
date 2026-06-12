---
title: "Question"
date: 2005-12-11
forum: General Help
---

### Post by DiscoKiller on 2005-12-11
if i`m running terminal, and by some miracle i make it to the directory i want (i`m not too skilled in the ol terminal you see) is there a way i can open the particular dir i want in a file viewer like nautilus or something. this would help me greatly as i`m lazy as hell......thx DK

---

### Post by zoiks on 2005-12-11
Due to your message title, I'd say you don't deserve a response ;) .&#12288;But anyhoo, the following line seems to work for me (note the backticks):

```
nautilus file://`pwd`
```

---

### Post by kaamos on 2005-12-11
Like this: ```
nautilus --no-desktop $(pwd)
```

Since this is annoying to type you can do this:
- write the above command to a text file called for example "openhere", and save it in your home directory
- right click on the "openhere" file and check the permissions for execute
- open a terminal and move the file to /usr/local/bin by: ```
sudo mv openhere /usr/local/bin/
```
-now you can use the "openhere" command in terminal

---

### Post by DiscoKiller on 2005-12-11
i think my title is perfectly justified thank you very much :P , it was afgterall a question was it not?.....anyways enough of the pseudo rivalry, you`re a genius....thank you....you made my life so much easier


thx DK

---


---
title: "Users and Groups problems"
date: 2006-01-10
forum: General Help
---

### Post by Gustav on 2006-01-10
The Users and Groups program won't start for me it just says:

"Configuration could not be read
An error occurd while running the backend script"
(roughly translated from swedish)

And if i run it from the terminal it says:
```
$ users-admin
Entity: line 341: parser error : Input is not proper UTF-8, indicate encoding !
Bytes: 0xF6 0x6E 0x73 0x73
      <comment>Gustav J\uffffnsson,,,</comment>
                        ^
```
and where it says \uffff it's a square

Does anyone know which file it's in.

Thank you.

---

### Post by lamego on 2006-01-10
Any ideas where that "Gustav J\uffffnsson" string came froom ?
I guess it includes a nonprintable char (the square) which is breaking the parsing...
If it is a real name from an user you added, just fix it by editing the file with:
sudo gedit /etc/passwd .

---

### Post by Gustav on 2006-01-10
Thank you, it worked.

(The malfunktioning letter was an &#246;, but I've changed name from J&#246;nsson to Andreasson so that isn't an issue any longer)

---

### Post by nkhansen on 2006-01-10
[QUOTE=Gustav]Thank you, it worked.

(The malfunktioning letter was an ö, but I've changed name from Jönsson to Andreasson so that isn't an issue any longer)[/QUOTE]

Now that is bug-fixing. If the system doesn't accept chars in your name, simply change your name. You MUST be a dedicated user! :D

---


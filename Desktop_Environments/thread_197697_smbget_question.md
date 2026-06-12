---
title: "smbget question"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Aulden on 2006-06-16
Hi all, 

Firstly, I am copying files over from one computer to another with the command smbget. My only question is how can I get the output logged into a text file. I've tried putting in the command and adding ' > log.txt at the end for example, but all it gives me is the workgroup and username and doesn't print any of the filenames that have been copied. I need a list of the files it copies (or doesn't copy when it fails)

Does anyone know how to do this??

Would be extremely helpful!!!

Aulden:confused:

---

### Post by kirsche on 2006-06-16
Hi, 

try the following:

smbget -u user -p password smb://<ip>/<share>/files >logfile.txt 2>&1

---

### Post by Aulden on 2006-06-16
Awesomeness!!! 

I'll give that a go! Thanks! 

Aulden!

---


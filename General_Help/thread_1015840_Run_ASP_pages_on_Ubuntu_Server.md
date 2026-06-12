---
title: "Run ASP pages on Ubuntu Server"
date: 2008-12-19
forum: General Help
---

### Post by CrusaderAD on 2008-12-19
Is it possible to run ASP pages on a Ubuntu Linux Server? Maybe there's a way to do it with Apache?

---

### Post by hyper_ch on 2008-12-19
chilliasp supports that... but why would anyone want that?

---

### Post by CrusaderAD on 2008-12-19
Unfortunately we live in a world where asp is already implemented and coverting everything over to a php environment would be... suicide. I saw this page that suggests mono:

[http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX](http://www.goitexpert.com/entry.cfm?entry=Run-ASP-and-NET-in-UBUNTU--and-Debian-LINUX)

I wonder if pages relying on a Microsoft SQL server would work... I guess you would need to point everything over to a windows box with the database, unless it's possible to put the data in a local mysql server.

---

### Post by lovelyvik293 on 2008-12-19
If you are using a linux machine you can't use the MS SQL Server.You have to use the mysql or orcle.

---

### Post by directhex on 2008-12-19
ASP and ASP.NET are entirely unrelated - the only commonality between them is the name.

Mono can help you with ASP.NET - only a very limited selection of things will give you ASP - and even then, not ASP written in VBscript ot JScript

---

### Post by CrusaderAD on 2008-12-19
Bummer. It would be cool to have a development linux server running all these apps.

---

### Post by directhex on 2008-12-19
ASP was discontinued by MS years ago - there's no interest in implementing a bad, discontinued language like ASP/VBscript

---


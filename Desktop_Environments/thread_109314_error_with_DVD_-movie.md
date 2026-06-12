---
title: "error with DVD -movie"
date: 2005-12-28
forum: Desktop Environments
---

### Post by clapton on 2005-12-28
I can't see movies on ubuntu, appears this error

[img]http://www.alojarfotos.com/images/clapton/error.jpg[/img]
```
marco@2l33t4U:~$ sudo apt-get install libdvdcss
A Ler Listas de Pacotes... Pronto
Construindo Árvore de Dependências... Pronto
O pacote libdvdcss não está disponível, mas é referenciado por outro pacote.
Isso pode significar que o pacote falta, ficou obsoleto ou
está disponível somente a partir de outra fonte
E: O pacote libdvdcss não tem candidato para instalação

```

On english, this lib is not avaiable but is reffer to another package




THx for future help

---

### Post by audax321 on 2005-12-28
To install libdvdcss2, put the PLF repositories available here: [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

in your /etc/apt/sources.list file. Then install libdvdcss2.

---

### Post by clapton on 2005-12-28
thx a lot :)

---


---
title: "[SOLVED] Emerald can't fetch themes :S"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by muddymind on 2008-01-13
Hi!

Recently I installed emerald but when I loaded it there was no theme to chose from... Vrunner default theme was already applied to the windows so I tried to fetch new themes but it didn't work...

If I try to fetch GPL themes it gives the following error in the console:
```
svn: Não foi possível conectar ao servidor 'svn.beryl-project.org': Ligação recusada

```
It says that it can't connect o the server  'svn.beryl-project.org': connection refused

If I try to fetch non-GPL themes it says:
```
Erro validando o certificado de servidor para 'https://svn.generation.no:443':
 - O certificado não foi emitido por uma autoridade confiável. Use sua
   impressão digital para validar o certificado manualmente!
 - O nome do servidor do certificado não bate.
 - O certificado expirou.
Informações do certificado:
 - Nome do servidor: www.generation.no
 - Validade: de Fri, 23 Jan 2004 15:37:06 GMT até Sat, 22 Jan 2005 15:37:06 GMT
 - Emissor: Webserver, The Next Generation, Elverum, Hedmark, NO
 - Impressão digital: e1:71:1c:fa:d2:2f:de:56:00:cf:73:e3:d8:9b:eb:99:a4:e5:9d:12
(R)ejeitar, aceitar (t)emporariamente ou aceitar (p)permanente? svn: Requisição PROPFIND falhou em '/emerald-themes'
svn: PROPFIND de '/emerald-themes': Verifica    o de servidor de certificado falhou: certificado expirou, certificado emitido por hostnome diferente, emissor n  o    confi  vel (https://svn.generation.no)
```
It says that the certificate expired... 

How do I get new themes?

[]

ps-I'm using the last hardy beta but It happened with gutsy too...

---

### Post by dentaku65 on 2008-01-13
You must import them manually. Here you can find some :-)
[http://www.compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=559f1e2786498c74eb17a52d14493707]("http://www.compiz-themes.org/index.php?xcontentmode=103&PHPSESSID=559f1e2786498c74eb17a52d14493707")

---

### Post by muddymind on 2008-01-13
well... I was afraid that you would say that :P

thanks anyway :)

---

### Post by d3k4y on 2008-06-07
There's a much easier way, just use a package from feisty.  It is explained in the howto at [http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2](http://hacktivision.com/index.php/2008/06/07/how-to-enhance-ubuntu-8-04-hardy-heron-e?blog=2)

Good luck.

---


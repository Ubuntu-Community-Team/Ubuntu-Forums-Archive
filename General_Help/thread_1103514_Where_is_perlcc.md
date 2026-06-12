---
title: "Where is perlcc?"
date: 2009-03-22
forum: General Help
---

### Post by steve c on 2009-03-22
I'm having an absurdly hard time figuring out which package contains perlcc:

```
steve$ apt-cache search perlcc
libperl-dev - Perl library: development files
steve$ apt-file search perlcc
perl-doc-html: /usr/share/doc/perl-doc-html/html/perlcc.html
```

[ libperl-dev filelist]("http://packages.ubuntu.com/intrepid/amd64/libperl-dev/filelist") doesn't actually contain perlcc. The apt-file search makes it seem like perlcc is not in any package. Is that right?

Google searches turn up people having problems *using* perlcc but nothing about finding perlcc.

---

### Post by snova on 2009-03-22
Looks like they removed it. A quick Google pulled up this:

[http://www.perlmonks.org/index.pl?node_id=654568](http://www.perlmonks.org/index.pl?node_id=654568)

---

### Post by steve c on 2009-03-22
> **snova said:**
> Looks like they removed it. A quick Google pulled up this:

[http://www.perlmonks.org/index.pl?node_id=654568](http://www.perlmonks.org/index.pl?node_id=654568)
Ah, that's too bad. It was handy. I guess I was searching for which package it was in rather than if it'd been removed. Thanks.

---


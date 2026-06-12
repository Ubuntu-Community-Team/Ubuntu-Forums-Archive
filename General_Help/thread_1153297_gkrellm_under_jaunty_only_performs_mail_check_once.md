---
title: "gkrellm under jaunty only performs mail check once"
date: 2009-05-08
forum: General Help
---

### Post by hellfroze on 2009-05-08
I've been using the mail builtin of gkrellm to invoke fetchmail at intervals to download my mail but as of my upgrade to jaunty (from hardy), this has stopped working properly. The mail check occurs at gkrellm launch, but never occurs again unless I manually invoke the check- server logs confirm that no pop access is occuring.

I'm using 'fetchmail --all --silent' as my "Mail fetch/check program" and I had not changed anything in my config before noticing that I wasn't getting my mail. There is no error indication anywhere that I can see, even when running gkrellm -d out of a terminal.

Is this working for anyone? Anyone have ideas how I could trace this problem?

This is the standard gkrellm-2.3.2 in jaunty.

---


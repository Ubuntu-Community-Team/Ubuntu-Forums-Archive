---
title: "Issue in Adding an outside Repository"
date: 2006-04-19
forum: Desktop Environments
---

### Post by MichaelZ on 2006-04-19
Hello,

I would like to add an outside repository to Synaptic Package Manager. I have read the [wiki document]("https://wiki.ubuntu.com/AddingRepositoriesHowto"), but there is written in the point 1 to click *New* to add a repository (see [here]("https://wiki.ubuntu.com/AddingRepositoriesHowto#head-0caff7c16cb7386ca2b058b75ce3242d9a12d617")). But AFAIK there is no *New* button:confused:.

Is this a documentation error?

Thank you very much.

Best wishes,
Michael

---

### Post by Ramses de Norre on 2006-04-19
sudo gedit /etc/apt/sources.list
Add it at the end of the file.

---

### Post by MichaelZ on 2006-04-19
[quote=Ramses de Norre]sudo gedit /etc/apt/sources.list
Add it at the end of the file.[/quote] 
Thank you very much for the answer:), but would it works with Synaptic? I do not really use (at least yet) apt.

Best wishes,
Michael

---

### Post by Ramses de Norre on 2006-04-19
The same sources.list file is used by synaptic and apt, so the repo is added to synaptic too.
And in fact I do have an Add button in settings > repositories.

---

### Post by MichaelZ on 2006-04-19
[quote=Ramses de Norre]The same sources.list file is used by synaptic and apt, so the repo is added to synaptic too.
And in fact I do have an Add button in settings > repositories.[/quote] 
Ok, I understand. Thank you for the explanation:).

Best wishes,
Michael

---


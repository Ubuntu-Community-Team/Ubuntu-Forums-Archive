---
title: "Turning Ubuntu to Kubuntu on Hoary: Messed"
date: 2008-06-30
forum: Desktop Environments
---

### Post by karthikb23 on 2008-06-30
Hi,
I would like to install the package 'kubuntu-desktop' on my Ubuntu.
However:
1. my Ubuntu is a Hoary.
2. No internet connection.

Hence i added the Hardy CDs for Ubuntu and Kubuntu to the sources.

However, the 'dpkg-query' does not find any package named 'kubuntu-desktop'.

I downloaded this metapackage and tried installing it. But it resulted in a partial install with lots of dependencies unsatisfied.

Can anyone please advice how do i get out of this mess?
Can i install 'kubuntu-desktop' or 'kde' using the Hardy CDs I have?

Thanks a lot for any help

---

### Post by Inxsible on 2008-06-30
Since you have the Hardy CDs with you, wouldn't it be more easier to just install Kubuntu Hardy ?

I hope you have Kubuntu CDs - if you have Ubuntu, you will not get kubuntu-desktop. Install ubuntu-desktop and then you will need internet to get kubuntu.

---

### Post by aysiu on 2008-06-30
1. Hoary should not be used. It is old and no longer receives security updates (though, I guess if you have no internet connection, security may not be as much of an issue for you)

2. You should not mix and match different versions (Hoary software with Hardy software, for example). Mixing amd matching will lead to breakage.

3. The Desktop CD does not contain the packages necessary to add to an existing installation. For that, you'd need the Alternate CD.

4. Since you appear to have the Desktop CD for Kubuntu Hardy, just back up your files and use it to install **over** (as in, this will replace completely what you have now) your current Hoary installation. The whole process takes about 20 minutes.

---

### Post by karthikb23 on 2008-06-30
Thanks a lot guys!
I will do so.

---

### Post by karthikb23 on 2008-07-01
After some more reading, i realized that the hoary install CDs were themselves alternate CDs. (having text based installer).

The Hardy CDs have a single CD which works as live as well as install CD.

I had'nt accounted for this difference and expected Hardy CDs to work the same way :)

Thanks again!

---

### Post by karthikb23 on 2008-07-01
Another Query:

I had downloaded a meta-package for 'kubuntu-desktop'.
Then i used the 'dpkg -i <>' to install it.

Now this package is obviously in a broken state with lots of unsatisfied dependencies.

Any idea how do i remove this package completely?

I tried the --purge option, but not of much help.
The package currently seems in a 'Pending' status in the repository.

Any help is appreciated.

Thanks!

---


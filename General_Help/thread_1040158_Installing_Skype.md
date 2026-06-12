---
title: "Installing Skype"
date: 2009-01-15
forum: General Help
---

### Post by jesuisbenjamin on 2009-01-15
Hello Forum,

Am trying to help my father (whom i recently converted to Ubuntu) to install Skype. After downloading the package (*.deb) from the website of Skype, and installing the package (by means of double-clicking) he obtains the following message:

dependency is not satisfiable:libqt4-core

What does this mean? What can i do about it?

Thanks

---

### Post by redilyn on 2009-01-15
You need to run the following in the terminal

```

sudo apt-get install libqt4-core

```

I suspect this may not work though.

If it doesn't you may want to enable the medibuntu repos. They included skype.

```

sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
sudo apt-get install skype

```

That should do it

---


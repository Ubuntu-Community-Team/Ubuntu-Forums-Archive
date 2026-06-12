---
title: "JAVA install"
date: 2008-12-19
forum: General Help
---

### Post by trendyabinash on 2008-12-19
How to install java so that I can use it in firefox.


I have install this one using the terminal code
[http://www.javadesign.info/SystemsHardware/OS/Ubuntu/install-java-on-ubuntu](http://www.javadesign.info/SystemsHardware/OS/Ubuntu/install-java-on-ubuntu)

I have not restarted my system, do I have to restart???

Or I have to install something else???

---

### Post by any.linux12 on 2008-12-19
If you want for java app in firefox go to:

(in the firefox window) Tool-> add-ons -> get add on -> and add the Java Console 6.0.02

should work! try it

---

### Post by jamesstansell on 2008-12-20
> **any.linux12 said:**
> If you want for java app in firefox go to:

(in the firefox window) Tool-> add-ons -> get add on -> and add the Java Console 6.0.02

should work! try it

The java console addon doesn't work with the newest java plugin (the npjp2 "plugin2" version).  But I guess it should work with the sun-java6-plugin that is currently in intrepid (ubuntu 8.10).  I don't have it installed to try.

---

### Post by jamesstansell on 2008-12-20
> **trendyabinash said:**
> How to install java so that I can use it in firefox.


I have install this one using the terminal code
[http://www.javadesign.info/SystemsHardware/OS/Ubuntu/install-java-on-ubuntu](http://www.javadesign.info/SystemsHardware/OS/Ubuntu/install-java-on-ubuntu)

I have not restarted my system, do I have to restart???

Or I have to install something else???

You might have to restart Firefox.

Did you install the sun-java6-plugin?

Does this help?

```

$ sudo update-java-alternatives -s java-6-sun

```

---

### Post by Therion on 2008-12-20
Enable the [Medibuntu repositories](https://help.ubuntu.com/community/Medibuntu) (you'll want them anyway) and then install **ubuntu-restricted-extras** via Synaptic.

---


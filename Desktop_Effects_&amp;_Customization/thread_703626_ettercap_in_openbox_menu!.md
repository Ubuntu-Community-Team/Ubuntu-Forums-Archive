---
title: "ettercap in openbox menu!"
date: 2008-02-21
forum: Desktop Effects &amp; Customization
---

### Post by openjoel on 2008-02-21
Hi,
I wanna start ettercap in gtk from my openbox menu.
The thing is, I dont know how.
Since ettercap needs to run as root to access the network devices.
I tried with running gksudo but it just wont start.

I dont get an error message or anything, its just like clicking on nothing!

The command I use at the moment is:
```

      <item label="Ettercap">
        <action name="Execute"><execute>gksudo ettercap -G</execute></action>
      </item>
```

It works to start other applications with gksudo, for example synaptic and update-manager.

Thanks / Joel

---

### Post by lidholm on 2008-02-22
I'm not sure this is going to help, but you can try to write gksudo "ettercap -G" instead, i.e. add the quotation marks. I've seen this problem appear with regular sudo in a console at least, so it might be worth a try?

// lidholm

---

### Post by openjoel on 2008-02-22
> **lidholm said:**
> I'm not sure this is going to help, but you can try to write gksudo "ettercap -G" instead, i.e. add the quotation marks. I've seen this problem appear with regular sudo in a console at least, so it might be worth a try?

// lidholm

Thanks it works now!

---

### Post by thedaemon on 2008-02-26
I do believe it's because you seed the arguement -G. If it was just gksudo ettercap I don't think it would be a problem.

---


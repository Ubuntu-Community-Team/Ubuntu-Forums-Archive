---
title: "How to do dicsless clinet  and run it with server"
date: 2009-05-02
forum: General Help
---

### Post by satiya on 2009-05-02
i am still very new to linux ubuntu...just 1 day 6 hours...i need to know how to do ..client pcs without hard dics and its runs with the server ....anyone pla advice me on  it

---

### Post by Carl Hamlin on 2009-05-02
> **satiya said:**
> i am still very new to linux ubuntu...just 1 day 6 hours...i need to know how to do ..client pcs without hard dics and its runs with the server ....anyone pla advice me on  it

Need a little more information.

Are you talking about straight dumb terminals, or is there a little wiggle room here?

---

### Post by satiya on 2009-05-02
well its how to explain .....hmmm....ok...i have 15 pc in my shop....all using hard dics...and i have read in a book where we dont need to use hard dics anymore ...we use server to run all 15 pc....when we use the server the 15 pcs dont use hard dics...it use server as image ...all the programs are istalled in server and this 15 pcs use server as its image

---

### Post by Carl Hamlin on 2009-05-02
> **satiya said:**
> well its how to explain .....hmmm....ok...i have 15 pc in my shop....all using hard dics...and i have read in a book where we dont need to use hard dics anymore ...we use server to run all 15 pc....when we use the server the 15 pcs dont use hard dics...it use server as image ...all the programs are istalled in server and this 15 pcs use server as its image

Hmm. There's a chance you're talking about something I've never heard of, but it *sounds* like you're talking about dumb terminals, in which case the connection software exists in firmware on the terminal hardware itself, and the use thereof will be covered in the terminal manual.

So far as using PCs with no drive, I don't know of a way to do that, unless you're using a modified BIOS with connection firmware on it. If you are, then the BIOS manual should have instructions as to how to enable the setting.

Barring that, however, PCs are designed to POST, then transfer control to a drive connected to the motherboard.

---

### Post by Kareeser on 2009-05-02
You will require a PXE-enabled network card on all client computers.

Server packages include: ltsp-server-standalone, dhcp3-server, tftpd-hpa, nfs-kernel-server

---

### Post by satiya on 2009-05-02
hmmm... i will find the way...u also try to find it...i think it run like that ...but i see a cyber cafe using it and they have the software and i forget the name of software ...i get the name of software which they are using ... i think it will will be very usefull......

---

### Post by Kareeser on 2009-05-02
This may help you out.

[https://help.ubuntu.com/community/Installation/OnNFSDrive](https://help.ubuntu.com/community/Installation/OnNFSDrive)

Not likely, though, since it's a very crudely written article.

---


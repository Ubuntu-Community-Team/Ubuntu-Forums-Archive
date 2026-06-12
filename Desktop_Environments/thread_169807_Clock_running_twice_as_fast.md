---
title: "Clock running twice as fast"
date: 2006-05-03
forum: Desktop Environments
---

### Post by Martin Pilka on 2006-05-03
Hello,

after the installation of Ubuntu 5.10 on my Acer Aspire 5024 WLMi notebook, my clock is running twice as fast as it should. Adding "noapic" to boot options solves the problem, but then i.e. my network card (Realtek RTL8139) works slower (1.4 MB/s vs 2.6 MB/s; even 2.6 MB/s sucks, but this issue I address in another email, "Realtek RTL8139 very slow").

Anybody knows how to let APIC enabled without side effects? (i.e. doubled clock speed).

Thanks,
Martin

---

### Post by frodon on 2006-05-03
This might help : [http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

---

### Post by Martin Pilka on 2006-05-03
Hello Frodon,

thanks for the tip! It seems that for 32bit Ubuntu (one I am using, in spite of fact I have AMD64 HW), only option is to disable apic by noapic option. However, this is fine for me.

Martin

---


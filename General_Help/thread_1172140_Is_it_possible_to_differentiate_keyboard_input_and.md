---
title: "Is it possible to differentiate keyboard input and barcode input in linux?"
date: 2009-05-28
forum: General Help
---

### Post by ellappan on 2009-05-28
Hi All,

I am using keyboard and barcode scanner and bar code scanners output always going to screen like a keyboard. Is it possible to differentiate these two? Because I want to put barcode readers output to some text file.

Please any idea will help me to proceed further...thanks

---

### Post by niteshifter on 2009-05-28
Hi,

How does the keyboard and scanner connect to the computer? There are two ways commonly used to connect a bar code scanner to a system:

A) The "Y" or sometimes called a wedge - this type combines scanner output with keyboard output.

B) By USB (older units: serial port).

If you have A, you're basically out of luck - there is no way to separate the two, the purpose of the Y / wedge is to make the scanner's output look like keyboard data. I suspect this is what you have.

However, don't give up just yet. Most wedge-connected scanners are really plain old RS232 serial output, the wedge adapter converts the electrical signals. If the scanner cord ends (at the wedge) is a 9 pin connector a USB to RS232 adapter will probably work - but a little bit of programming will be required to read from this pseudo serial port.

---

### Post by ellappan on 2009-05-28
> **niteshifter said:**
> Hi,

How does the keyboard and scanner connect to the computer? There are two ways commonly used to connect a bar code scanner to a system:

A) The "Y" or sometimes called a wedge - this type combines scanner output with keyboard output.

B) By USB (older units: serial port).

If you have A, you're basically out of luck - there is no way to separate the two, the purpose of the Y / wedge is to make the scanner's output look like keyboard data. I suspect this is what you have.

However, don't give up just yet. Most wedge-connected scanners are really plain old RS232 serial output, the wedge adapter converts the electrical signals. If the scanner cord ends (at the wedge) is a 9 pin connector a USB to RS232 adapter will probably work - but a little bit of programming will be required to read from this pseudo serial port.
Hi,

Thanks a lot for your help. My scanner connected through USB port. keyboard also connected through USB interface.

---


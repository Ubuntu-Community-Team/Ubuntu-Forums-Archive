---
title: "Can someone explain Big-Endian and Little-Endian to me?"
date: 2008-05-09
forum: Education &amp; Science
---

### Post by Jordanwb on 2008-05-09
I'm currently working on a simple MP3 Library program in C# (using Mono). I'm using an article on Code Project (search "Mpeg Audio Header" it's the first one) and it mentions "Big Endian WORD" and "Big Endian DWORD", I looked up Big Endian on Wikipedia and I don't understand the article. Can someone plainly explain Big Endian and Little Endian to me?

Thanks.

---

### Post by croto on 2008-05-09
Hey,

let me try give an explanation based on the decimal system. The binary case is the same.

Imagine you have boxes, numbered 0, 1, 2, 3, etc. In each one of these boxes, you can store a two-digits number, for example, 01, 23, 86, etc. This represents the computer memory. So these boxes are good for storing numbers up to 99, but now, how do we store larger numbers? One possible way is splitting the number in two-digits parts. For instance, suppose we want to store the number 6952. We can split it in the parts "69" and "52". Then we can store "69" in box 0, and "52" in box 1. Or we can store "52" in box 0, and "69" in box 1. The first case is called Big Endian order, and the second case is called Little Endian order.

In binary, each box (memory address) can store 8 binary digits (8 bits). So if you want to sore the number 010111010 11111111 01011101 11011001 (I already split the number in 8-bits parts), you can store the first part in memory address x, the second part in address x+1, and so on, and thats big endian. Reversing the order: last part in mem addr x, third part in mem addr x+1 ... first part in mem addr x+3, gives little endian.

Does that make more sense?

Intel processors use little endian ordering, Power PC use big endian.

---

### Post by mrsteveman1 on 2008-05-09
Its byte ordering, one is forward, the other is backward :D

---

### Post by Jordanwb on 2008-05-09
Okay so let's take the number 3602891615

in binary 3602891615 would be 11010110 10111111 11000011 01011111

So in a four byte array in Big Endian it would be like this:

array[0] = 214 (11010110)
array[1] = 191 (10111111)
array[2] = 195 (11000011)
array[3] = 95 (01011111)

But in Little Endian it would be:


array[0] = 95 (01011111)
array[1] = 195 (11000011)
array[2] = 191 (10111111)
array[3] = 214 (11010110)

Also what does WORD and DWORD mean? I know that in Basic a word type variable is a unsigned 16 bit integer so would it be the same in this case? Would DWORD be a 16 bit signed integer?

---

### Post by croto on 2008-05-09
Exactly. You can actually verify that it works the way you're saying by saving a binary file containing that number and viewing it with a hex editor. 

Conventionally, people use WORD to refer to a 16 bits variable or data, and DWORD refers to a double WORD, that is, 32 bits of data (independently from the data type. For example, a DWORD can be a "float", "int", "unsigned int", which are 32 bits long).

---

### Post by Jordanwb on 2008-05-09
All right cool. I was always wondering why BitConverter.GetBytes () in C# returned an array of bytes where the order was reversed.

Thanks.

---


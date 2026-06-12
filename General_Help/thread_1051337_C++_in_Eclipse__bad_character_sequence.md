---
title: "C++ in Eclipse  bad character sequence"
date: 2009-01-26
forum: General Help
---

### Post by Lostin60's on 2009-01-26
Absolute newbie here. My first use of eclipse, and my first C++.
I am using the introduction guides "Hello World" program. Here is what I have coded.
```
#include <iostream>
int main()
{
	//say hello 5 times
	for (int index=0; index < 5; ++index)
		cout << "HelloWorld!!" << endl;
	
		char [COLOR="Red"]input=`1`[/COLOR];
```
In red is the problem. When I hover over it I get (bad character sequence encountered:`). But since it is straight from the guide, I assume it is correct. Any and all help will be appreciated.
I hit the same problem with `m`. It is the (`) that is the problem. Comeau says
> "ComeauTest.c", line 9: error: unrecognized token
  	char input = `i`;


[COLOR="White"]aa[/COLOR]

---

### Post by snova on 2009-01-26
Those look like backticks, they should be single quotes: '

---

### Post by Lostin60's on 2009-01-26
> **snova said:**
> Those look like backticks, they should be single quotes: '

They are single quotes in the source code. This is it, just like the guide.
```
/*
 * main.cpp
 *
 *  Created on: Jan 26, 2009
 *      Author: daniel
 */
#include <iostream>
using namespace std;

int main(){
	//say hello 5 times
	for(int index = 0; index < 5; ++index)
	cout << "HelloWorld!" << endl;

	char input = `i`;

	cout << "To exit, press `m`" << endl;

	while(input != `m`){
		cin >> input;
		cout << "You just entered" << input
			<< "You need to enter m to exit." << endl;
	}

	exit(0);

}
```
And here is the error output
```
Description	Resource	Path	Location	Type
&#8216;exit&#8217; was not declared in this scope	main.cpp	Hello	25	C/C++ Problem
&#8216;i&#8217; was not declared in this scope	main.cpp	Hello	15	C/C++ Problem
&#8216;m&#8217; was not declared in this scope	main.cpp	Hello	19	C/C++ Problem
make: *** [main.o] Error 1	Hello		0	C/C++ Problem
stray &#8216;`&#8217; in program	main.cpp	Hello	15	C/C++ Problem
stray &#8216;`&#8217; in program	main.cpp	Hello	19	C/C++ Problem

```
I think the compiler disagrees with the environment. When you right click a line of code you get a quick fix option. However, when you choose the quick fix it has no suggestions to fix the error. It seems the compiler doesn't like the single quote. If you have any suggestions, please feel free to comment.

Well, hell, in previewing this post, it looks as if...well let me look  really dumb here. When you said "backtics" I thought you were being humorous. I have never heard the term. I assumed the mark below the tilda was a single quote. It isn't, is it? I am looking for a way to type one now. Well, don't I just feel like a moron! lol

Sometimes I worry about me, I really do. In the heat of learning something, I sometimes forget things I have known for years. I know where a single quote is, I've known it since I was a kid. But it went away. My mind just plain deleted that file. So, I looked to what I was learning to figure out the problem, because that is where I was focused. Well, about the 15th time I looked at the quote key, the trash bin opened and I found my deleted file. Anyway, I think I have it under control now. And, please, feel free to laugh...I damn sure would.
[COLOR="White"]aa[/COLOR]

---


---
title: "trouble installing android"
date: 2009-04-03
forum: General Help
---

### Post by agim on 2009-04-03
I followed the how-tos, everything worked fine. Until I ran the hello world code. I copied and pasted the code, so it should be right. All I get is this uninformative warning.

Your project contains error(s), please fix them before running your application.

I ran one of the demo's as well (testrun), and all I get the same error.

Please help!

Here is the code I am running, just in case.

package com.android.hello;

import android.app.Activity;
import android.os.Bundle;
import android.widget.TextView;

public class HelloAndroid extends Activity {
   /** Called when the activity is first created. */
   @Override
   public void onCreate(Bundle savedInstanceState) {
       super.onCreate(savedInstanceState);
       TextView tv = new TextView(this);
       tv.setText("Hello, Android");
       setContentView(tv);
   }
}

---


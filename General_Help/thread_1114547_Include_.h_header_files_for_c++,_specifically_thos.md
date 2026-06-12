---
title: "Include .h header files for c++, specifically those for ITK"
date: 2009-04-02
forum: General Help
---

### Post by vancouverite on 2009-04-02
Hi all,
I'm learning to program C++ so that I can use the Insight Toolkit ([www.itk.org](www.itk.org)) for image analysis.

Ubuntu has insighttoolkit, insighttoolkit-dev and insighttoolkit-examples in the repositories (which is sweet) and when I install them the .h headerfiles are stored in 8 folders under /usr/include/InsightToolkit/ (eg .../InsightToolkit/Common/ and .../InsightToolkit/Utilities/, etc)

The problem that I'm having is that gcc doesn't look into these directories when compiling. So if I use the headers

#include "itkImageFileReader.h"
#include "itkImageFileWriter.h"

it won't work (these are kept in the .../InsightToolkit/IO/ folder).  If I use the full path like this:

#include "/usr/include/InsightToolkit/itkImageFileReader.h"
#include "/usr/include/InsightToolkit/itkImageFileWriter.h"

it runs into problems that these link to other .cxx files that have headers in .../Common/ or .../Utilities/.  Since  I can't re-write the header of every ITK file, there must be a way for gcc (or Geany which I'm using for the editing) to discover all of these headers.  How do I do that?

I can get it to compile using cmake, but this is a pain as I really don't know what I'm doing in cmake and I don't need the cross-platform utility that it provides.

Thanks for your help ahead of time!

Van

PS here is the code that I'm compiling.  It's the image converter, straight from the ITK manual:

```
#include "itkImageFileReader.h"
#include "itkImageFileWriter.h"
#include "itkImage.h"

int main(int argc, char** argv)
{
	if (argc < 3 )
	{
		std::cout << "Usage: " << std::endl;
		std::cout << argv[0] << " inputImageFile outputImageFile" << std::endl;
		return EXIT_FAILURE;
	}
	
	typedef itk::RGBPixel<unsigned char> PixelType;
	const	unsigned int Dimension = 2;
	typedef itk::Image< PixelType, Dimension > ImageType;
	
	typedef itk::ImageFileReader< ImageType > ReaderType;
	typedef itk::ImageFileWriter< ImageType > WriterType;
	
	ReaderType::Pointer reader = ReaderType::New();
	WriterType::Pointer writer = WriterType::New();
	
	const char * inputFilename = argv[1];
	const char * outputFilename = argv[2];
	
	reader->SetFileName( inputFilename  );
	writer->SetFileName( outputFilename );
	
	writer->SetInput ( reader->GetOutput() );
	
	try{
		writer->Update();
	}
	catch( itk::ExceptionObject & err )
	{
		std::cout << "ExceptionObject caught!" << std::endl;
		std::cout << err << std::endl;
		return EXIT_FAILURE;
	}
	
	return EXIT_SUCCESS;
}
```

---


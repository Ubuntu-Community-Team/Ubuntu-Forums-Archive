---
title: "C++ factory method pattern and data abstraction"
date: 2023-01-18
forum: Education &amp; Science
---

### Post by ronakmehta on 2023-01-18
I'm attempting to implement the Factory Method Pattern in C++ while maintaining a high degree of abstraction. All derived classes are in the same file in the sample supplied in the link, although this is not always the case.
Without header files for derived classes: I didn't provide a header file for the derived class (declaration & definition in the source file) to keep implementation details, so I don't see how to implement the factory method because the derived classes are not visible and forward declaration is not possible.
My code:
```
//graphic-api.hpp
class GraphicApi {
public:

    enum class Type {
        //OPENGL,
        //DIRECTX,
        VULKAN
    };

    virtual void render() = 0;
    virtual ~GraphicApi() {};

    static std::unique_ptr<GraphicApi> make(const Window& window, Type type);

};

//graphic-api.cpp 

//need to include headers for derived classes
std::unique_ptr<GraphicApi> GraphicApi::make(const Window& window, GraphicApi::Type type) {
    switch (type) {
    case GraphicApi::Type::VULKAN:
        return std::make_unique<VulkanApi>(window);
    default:
        assert(0 && "Unsupported Graphic API");
    }
    return nullptr;
}

//vulkan-api.hpp
class VulkanApi : public GraphicApi {
public:
    VulkanApi(const Window& window);
    virtual void render() {};

private:

    // lot of private members & methods related to Vulkan API (not nice to see here)     
    vk::UniqueInstance instance;
    ... };
```
In example 2), perhaps utilising the [PImpl idom]("https://en.cppreference.com/w/cpp/language/pimpl") can help fix the problem, however I'm not sure whether this is the correct/reasonable method. What is the most common/best method for implementing this pattern in C++?
I can construct the factory method as proposed [here]("https://www.scaler.com/topics/cpp/abstraction-in-cpp/"), however the implementation details of derived classes leak since the private members and functions must be mentioned in the header.

---


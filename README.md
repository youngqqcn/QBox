# QBox
收集实用的,优秀的开源库; 

<https://github.com/rigtorp/awesome-modern-cpp>



## 适合源码学习优秀的开源项目

- cJson <https://github.com/DaveGamble/cJSON>
- <https://github.com/Alinshans/MyTinySTL>
- <https://github.com/EZLippi/Tinyhttpd>

## 有趣的项目

- 俄罗斯方块 <https://github.com/taylorconor/tinytetris>



## 项目开发会用到项目

### 日志

- C++  https://github.com/gabime/spdlog
- Python <https://github.com/Delgan/loguru>





### JSON

<https://nlohmann.github.io/json/>  非常好用



```cpp
// TestJson.cpp : 定义控制台应用程序的入口点。
//

#include "stdafx.h"
#include <vector>
#include <iostream>
#include <nlohmann/json.hpp>
using namespace std;
using namespace nlohmann;



namespace ns {
	// a simple struct to model a person
	struct person {
		std::string name;
		std::string address;
		int age;
	};
}

int main()
{
	std::vector<int> c_vector{ 1, 2, 3, 4 };
	json j_vec(c_vector);

	std::cout << j_vec.dump() << std::endl; //[1, 2, 3, 4] 


	json j_original = R"({
  "baz": ["one", "two", "three"],
  "foo": "bar"
})"_json;

	std::cout << j_original["/baz/1"_json_pointer] << std::endl; //"two"


	{

		ns::person p = { "Ned Flanders", "744 Evergreen Terrace", 60 };

		// convert to JSON: copy each value into the JSON object
		json j;
		j["name"] = p.name;
		j["address"] = p.address;
		j["age"] = p.age;

		//std::cout << j.dump() << std::endl;
		std::cout << j << std::endl;

		// ...
		{
			// convert from JSON: copy each value from the JSON object
			ns::person p{
				j["name"].get<std::string>(),
				j["address"].get<std::string>(),
				j["age"].get<int>()
			};


			std::cout << p.name << "  " << p.address << "  " << p.age << std::endl;
		}
	}

	system("pause");
    return 0;
}


```





### 格式化

<https://github.com/fmtlib/fmt>



### Web框架

- C++ <https://github.com/chenshuo/muduo/>  陈硕大神

- C++ <https://github.com/oatpp/oatpp>
- C++ <https://github.com/an-tao/drogon>
- C++  <https://github.com/qicosmos/cinatra>  国内开发

- Rust <https://github.com/actix/actix-web> 
- Golang <https://github.com/bilibili/kratos> bilibili基于gin二次开发
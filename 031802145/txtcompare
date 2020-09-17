#ifndef _GLIBCXX_NO_ASSERT
#include <cassert>
#endif
#include <cctype>
#include <cerrno>
#include <cfloat>
#include <ciso646>
#include <climits>
#include <clocale>
#include <cmath>
#include <csetjmp>
#include <csignal>
#include <cstdarg>
#include <cstddef>
#include <cstdio>
#include <cstdlib>
#include <cstring>
#include <ctime>

#if __cplusplus >= 201103L
#include <ccomplex>
#include <cfenv>
#include <cinttypes>
#include <cstdalign>
#include <cstdbool>
#include <cstdint>
#include <ctgmath>
#include <cwchar>
#include <cwctype>
#endif

// C++
#include <algorithm>
#include <bitset>
#include <complex>
#include <deque>
#include <exception>
#include <fstream>
#include <functional>
#include <iomanip>
#include <ios>
#include <iosfwd>
#include <iostream>
#include <istream>
#include <iterator>
#include <limits>
#include <list>
#include <locale>
#include <map>
#include <memory>
#include <new>
#include <numeric>
#include <ostream>
#include <queue>
#include <set>
#include <sstream>
#include <stack>
#include <stdexcept>
#include <streambuf>
#include <string>
#include <typeinfo>
#include <utility>
#include <valarray>
#include <vector>

#if __cplusplus >= 201103L
#include <array>
#include <atomic>
#include <chrono>
#include <condition_variable>
#include <forward_list>
#include <future>
#include <initializer_list>
#include <mutex>
#include <random>
#include <ratio>
#include <regex>
#include <scoped_allocator>
#include <system_error>
#include <thread>
#include <tuple>
#include <typeindex>
#include <type_traits>
#include <unordered_map>
#include <unordered_set>
#endif
using namespace std;
namespace cosine
{
	bool wordsegment(const std::string& substr)
	{
		return true;
	}
	float txtcompare(const std::string& str1, const std::string& str2)
	{
		std::map<std::string, std::pair<size_t, size_t> > container;
		for (size_t i = 0, begin = 0; i < str1.length(); ++i)
		{
			std::string substr = str1.substr(begin, i - begin + 1);
			if (wordsegment(substr))
			{
				++container[substr].first;
				begin = i + 1;
			}
		}

		for (size_t i = 0, begin = 0; i < str2.length(); ++i)
		{
			std::string substr = str2.substr(begin, i - begin + 1);
			if (wordsegment(substr))
			{
				++container[substr].second;
				begin = i + 1;
			}
		}

		unsigned long pro = 0;
		unsigned long mo1 = 0;
		unsigned long mo2 = 0;

		for (std::map<std::string, std::pair<size_t, size_t> >::const_iterator it = container.begin(); it != container.end(); ++it)
		{
			const std::pair<size_t, size_t>& cnt = it->second;
			pro += cnt.first * cnt.second;
			mo1 += cnt.first * cnt.first;
			mo2 += cnt.second * cnt.second;
		}

		return pro / (std::sqrt(static_cast<float>(mo1)) * std::sqrt(static_cast<float>(mo2)));
	}
}	//cos
using namespace cosine;

//从文件中读文本存入字符串中
string file_string(char * filename)
{
	ifstream ifile(filename);
	//将文件读入到ostringstream对象buf中
	ostringstream buf;
	char ch;
	while (buf&&ifile.get(ch))
		buf.put(ch);
	//返回与流对象buf关联的字符串
	return buf.str();
}

int main()
{
	//文件名
	char fn1[] = "orig.txt";
	char * fn = fn1;
	string str1;
	str1 = file_string(fn);
	char fn2[] = "null.txt";
	char * fnn = fn2;
	string str2;
	str2 = file_string(fnn);
	ofstream fout;
	fout.open("output.txt");
	fout << cosine::txtcompare(str1, str2);
	fout.close();
	system("pause");
}

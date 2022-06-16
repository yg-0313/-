# -
记录平时学习中遇到的问题
#include<stdio.h>
//int main()
//{
//	int ret = 0;
//	char password[20] = { 0 };
//	printf("请输入密码：\n");
//	scanf("%s", password);//输入
//	printf("请确认(Y\N):\n");
//	ret = getchar();//Y\N
//	if ('Y' == ret)
//	{
//		printf("确认成功\n");
//	}
//	else
//	{
//		printf("放弃确认\n");
//	}
//	return 0;
//}
//这个代码在运行的时候会发现问题，还没有输入Y\N便直接输出了放弃确认
int main()
{
	int ret = 0;
	char password[20] = { 0 };
	printf("请输入密码：\n");
	scanf("%s", password);//输入
	while (getchar() != '\n')
	{}
	printf("请确认(Y\N):\n");
	ret = getchar();//Y\N
	if ('Y' == ret)
	{
		printf("确认成功\n");
	}
	else
	{
		printf("放弃确认\n");
	}
	return 0;
}
//出现错误的原因是，在没有使用while (getchar() != '\n')语句的时候，
//缓冲区内因为我们输入密码使用了回车，所以getchar会读取'\n'其对应
//的ASCLL码为10所以不满足if判断语句，直接输出放弃确认。但在使用了
//while (getchar() != '\n')语句后，会自动读取到'\n'后才会自动跳出
//循环，所以这里可以用while (getchar() != '\n')语句解决问题

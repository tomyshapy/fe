# fe#include <stdio.h>
#include <graphics.h>
#include <conio.h>
#include <stdlib.h>
#include <math.h>

void main()
{
	int gdrv = DETECT, gmode, errorcode, mx, my;
	float x, y, k, kx;
	initgraph(&gdrv, &gmode, "..\\BGI");
	errorcode = graphresult();
	if (errorcode != grOk)
	{
		printf("Graphics error : %s\n", grapherrormsg(errorcode));
		printf("Press any key to halt ...");
		getch();
		exit(1);
	}

	mx = getmaxx() / 2;
	my = getmaxy() / 2;
	x = 0;
	kx = 2 *M_PI / mx;
	setbkcolor(BLUE);
	setcolor(WHITE);
	line(0, my, 2 *mx, my);
	line(mx, 0, mx, 2 *my);
	moveto(mx, 0);
	linerel(7, 7);
	moveto(mx, 0);
	linerel(-7, 7);
	moveto(2 *mx, my);
	linerel(-7, -7);
	moveto(2 *mx, my);
	linerel(-7, 7);
	setcolor(RED);
	k = 100;
	while (x < mx *2 - 10)
	{
		y = k* sin((x - mx) *kx);
		putpixel((int) floor(x), my - (int) floor(y), RED);
		x = x + 0.1;
	}

	settextstyle(1, 0, 2);
	setcolor(LIGHTGREEN);
	outtextxy(50, 10, "Do Thi Ham So");
	outtextxy(50, 40, " y = Sin(x)");
	settextstyle(2, 0, 5);
	outtextxy(mx + 7, my + 5, "0");
	line(mx + mx / 4, my - 2, mx + mx / 4, my + 2);
	line(mx - mx / 4, my - 2, mx - mx / 4, my + 2);
	line(mx / 4, my - 2, mx / 4, my + 2);
	line(2 *mx - mx / 4, my - 2, 2 *mx - mx / 4, my + 2);
	line(mx - 2, my - 100, mx + 2, my - 100);
	line(mx - 2, my + 100, mx + 2, my + 100);
	outtextxy(mx - 13, my - 107, "1");
	outtextxy(mx - 20, my + 90, "-1");
	moveto(mx + mx / 2 - 4, my + 17);
	lineto(mx + mx / 2 - 4, my + 9);
	lineto(mx + mx / 2 + 1, my + 9);
	lineto(mx + mx / 2 + 1, my + 17);
	moveto(mx / 2 - 4, my + 17);
	lineto(mx / 2 - 4, my + 9);
	lineto(mx / 2 + 1, my + 9);
	lineto(mx / 2 + 1, my + 17);
	line(mx / 2 - 10, my + 12, mx / 2 - 7, my + 12);
	getch();
	closegraph();
}

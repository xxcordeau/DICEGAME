# DICEGAME
🎲 콘솔창으로 주사위게임을 해보자 🎲

- 조건
    - 돈을 넣는다 (500원에 1게임,1000원에 2게임…)
    - 주사위 더블 시 점수 2배 / 한번 더
    - 주사위 연속 더블 시 돈과 기회 초기화( 0으로 )
    - 남은 돈 이용

![Untitled](https://github.com/xxcordeau/DICEGAME/assets/117654698/4ef02046-7cd6-4d6e-9460-1120cd56bdff)


package class01;

import java.util.Random;
import java.util.Scanner; //command+shift+o

public class Test01 {

	public static void main(String[] args) {
		Scanner sc =  new Scanner (System.in); 
		Random random = new Random();
		Thread tr = new Thread();
		
		
		// 필요한 변수 
		int coin = 0; 
		boolean end = false; // 사용자의 게임 진행/ 종료 여부 ( 플래그 변수 ) 
		String ans = "";
		String one = "				┌─────────┐\n"+  
		             "				│         │\n"+  
		             "				│    ●    │\n"+  
		             "				│         │\n"+  
		             "				└─────────┘\n";
		String two = "				┌─────────┐\n"+  
		             "				│  ●      │\n"+  
		             "				│         │\n"+  
		             "				│      ●  │\n"+  
		             "				└─────────┘\n";
		String three = "				┌─────────┐\n"+  
			           "				│ ●       │\n"+  
			           "				│    ●    │\n"+  
			           "				│       ● │\n"+  
			           "				└─────────┘\n";
		String four = "				┌─────────┐\n"+  
		              "				│ ●     ● │\n"+  
		              "				│         │\n"+  
		              "				│ ●     ● │\n"+  
		              "				└─────────┘\n";
		String five = "				┌─────────┐\n"+  
	                  "				│ ●     ● │\n"+  
	                  "				│    ●    │\n"+  
	                  "				│ ●     ● │\n"+  
	                  "				└─────────┘\n";
		String six = "				┌─────────┐\n"+  
	                 "				│ ●  ●  ● │\n"+  
	                 "				│         │\n"+  
	                 "				│ ●  ●  ● │\n"+  
	                 "				└─────────┘\n";
		
      //System.out.println(one + two + three + four + five + six);

		
		int dice1;
		int dice2;
		
		
		while(true) {
			
			System.out.println("==========================================================================");
			System.out.println("||                                                                      ||\n"
					+ "||  ██████╗ ██╗ ██████╗███████╗     ██████╗  █████╗ ███╗   ███╗███████╗ ||\n"
					+ "||  ██╔══██╗██║██╔════╝██╔════╝    ██╔════╝ ██╔══██╗████╗ ████║██╔════╝ ||\n"
					+ "||  ██║  ██║██║██║     █████╗      ██║  ███╗███████║██╔████╔██║█████╗   ||\n"
					+ "||  ██║  ██║██║██║     ██╔══╝      ██║   ██║██╔══██║██║╚██╔╝██║██╔══╝   ||\n"
					+ "||  ██████╔╝██║╚██████╗███████╗    ╚██████╔╝██║  ██║██║ ╚═╝ ██║███████╗ ||\n"
					+ "||  ╚═════╝ ╚═╝ ╚═════╝╚══════╝     ╚═════╝ ╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝ ||\n"
					+ "||                                                                      ||\n"
					+ "||                                                                      ||");
			System.out.println("==========================  PLEASE INSERT COIN  ==========================");
			coin += sc.nextInt(); // 금액 누적( += ) / 잔액을 남기기 위함
			System.out.println("COIN : "+ coin); // 코인값 출력
			
			System.out.println("=============================  START GAME  ===============================");
			System.out.println("");
			int score = 0; //점수 합계 
			int cnt = 0; // 회차
			
			
			while( coin >= 500 ) { //코인이 500이상이거나 같을 경우 반복 실행 
				
				int setScore = 0; //회차별 점수
				
				if(cnt != 0) { // 회차가 0이 아닐 경우 아래의 내용 출력 
				System.out.println("==========================================================================");
				System.out.println("");
				}
				
				dice1 = random.nextInt(6)+1; 
				dice2 = random.nextInt(6)+1;
				
				String show1 =""; //주사위 텍스트 그림 초기화
				String show2 ="";
				
				if(dice1 == 1) {  // 주사위1 변환 
					show1 = one;
				}
				else if( dice1 == 2 ) { 
					show1 = two;
				}
				else if( dice1 == 3 ) {
					show1 = three;
				}
				else if( dice1 == 4 ) {
					show1 = four;
				}
				else if( dice1 == 5 ) {
					show1 = five;
				}
				else if( dice1 == 6 ) {
					show1 = six;
				}
				
				if(dice2 == 1) {  //주사위2 변환
					show2 = one;
				}
				else if( dice2 == 2 ) {
					show2 = two;
				}
				else if( dice2 == 3 ) {
					show2 = three;
				}
				else if( dice2 == 4 ) {
					show2 = four;
				}
				else if( dice2 == 5 ) {
					show2 = five;
				}
				else if( dice2 == 6 ) {
					show2 = six;
				}
				
				
				
				if (dice1==dice2) {   // 더블일 경우 카운트 , 돈 차감 x
					
					System.out.println( show1  + show2 + "\n" + "			>> DOUBLE , THROW AGAIN <<");
					System.out.println(""); // 더블일경우 주사위 1 + 2출력 
					
					dice1 = dice1*2;
					dice2 = dice2*2;
					
					setScore = dice1 + dice2; //더블 값
					
					
					dice1 = random.nextInt(6)+1;
					dice2 = random.nextInt(6)+1;
					
					
					
					if(dice1 == 1) { //주사위 1변환
						show1 = one;
					}
					else if( dice1 == 2 ) {
						show1 = two;
					}
					else if( dice1 == 3 ) {
						show1 = three;
					}
					else if( dice1 == 4 ) {
						show1 = four;
					}
					else if( dice1 == 5 ) {
						show1 = five;
					}
					else if( dice1 == 6 ) {
						show1 = six;
					}
					
					if(dice2 == 1) { // 주사위 2 변환
						show2 = one;
					}
					else if( dice2 == 2 ) {
						show2 = two;
					}
					else if( dice2 == 3 ) {
						show2 = three;
					}
					else if( dice2 == 4 ) {
						show2 = four;
					}
					else if( dice2 == 5 ) {
						show2 = five;
					}
					else if( dice2 == 6 ) {
						show2 = six;
					}
					
				
					

          
					if ( dice1 == dice2 ) { // 주사위가 더블내에서 더블이 한 번 더 나왔울 경우 (더블+더블)
						if(dice1 == 1) { // 주사위1 변환
							show1 = one;
						}
						else if( dice1 == 2 ) {
							show1 = two;
						}
						else if( dice1 == 3 ) {
							show1 = three;
						}
						else if( dice1 == 4 ) {
							show1 = four;
						}
						else if( dice1 == 5 ) {
							show1 = five;
						}
						else if( dice1 == 6 ) {
							show1 = six;
						}
						
						if(dice2 == 1) { //주사위2 변환
							show2 = one;
						}
						else if( dice2 == 2 ) {
							show2 = two;
						}
						else if( dice2 == 3 ) {
							show2 = three;
						}
						else if( dice2 == 4 ) {
							show2 = four;
						}
						else if( dice2 == 5 ) {
							show2 = five;
						}
						else if( dice2 == 6 ) {
							show2 = six;
						}
						
						System.out.println( show1 + show2); 
						System.err.println("\n" + "	      	          >> DOUBLE & DOUBLE <<");
						System.err.println("\n"
								+ "  ██████╗  █████╗ ███╗   ███╗███████╗     ██████╗ ██╗   ██╗███████╗██████╗ \n"
								+ " ██╔════╝ ██╔══██╗████╗ ████║██╔════╝    ██╔═══██╗██║   ██║██╔════╝██╔══██╗\n"
								+ " ██║  ███╗███████║██╔████╔██║█████╗      ██║   ██║██║   ██║█████╗  ██████╔╝\n"
								+ " ██║   ██║██╔══██║██║╚██╔╝██║██╔══╝      ██║   ██║╚██╗ ██╔╝██╔══╝  ██╔══██╗\n"
								+ " ╚██████╔╝██║  ██║██║ ╚═╝ ██║███████╗    ╚██████╔╝ ╚████╔╝ ███████╗██║  ██║\n"
								+ "  ╚═════╝ ╚═╝  ╚═╝╚═╝     ╚═╝╚══════╝     ╚═════╝   ╚═══╝  ╚══════╝╚═╝  ╚═╝\n"
								+ "                                                                           \n"
								+ " ");
						score = 0; // 더블 두번 시 점수 초기화 (0점)
						coin = 0; // 더블 두번 시 금액 초기화 (0원)
						break; // 게임 종료 
					}
					
					
				}
				System.out.println( show1 + show2 ); 
				
				setScore += dice1 + dice2; // 각 회차별 점수 
				score += setScore; // 총합 = 주사위의 합
				System.out.println ( cnt + 1 + "SET : " + setScore ); // 각 회차별 점수
				
				
				coin -= 500; //종료조건 (금액차감)
				cnt++; // 회차
				
	
			}
			
			System.out.println("SCORE : " + score ); // 총합 출력
			
			
			while(true) { //게임이 끝날 경우 
				System.out.println("게임을 더 하시겠습까? 더 하시려면 y 종료하시려면 n를 입력해주세요. ");
				ans = sc.next();
				
				if( ans.equals("n") ) {
					end = true;
					
					break;
				}
				
				else if( ans.equals("y")) {
					end = false; 
					System.out.println("COIN : " + coin );
					break;
				}
				
				else {
					System.out.println("잘못입력하셨습니다.");
				}
			}
			
			
			if(end) {
				System.out.println("게임을 종료합니다.");
				break;
			}
			
		}


	}

}




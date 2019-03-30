# fly_to_cart_animation

Step 1. Add the JitPack repository to your build file

Add it in your root build.gradle at the end of repositories:

        allprojects {
            repositories {
              ...
              maven { url 'https://www.jitpack.io' }
            }
          }
          
          
Step 2. Add the dependency

        dependencies {
                  implementation 'com.github.posakya:fly_to_cart_animation:0.1'
            }
            
            
Step 3. Design your layout (You can see an example below)

                     <RelativeLayout
                            android:id="@+id/cartRelative"
                            android:layout_gravity="center_vertical|end"
                            android:layout_width="wrap_content"
                            android:layout_height="wrap_content"
                            android:layout_alignParentRight="true"
                            android:layout_centerVertical="true"
                            android:clickable="true"
                            android:paddingRight="3dip">

                            <ImageButton
                                android:id="@+id/cartButton"
                                android:layout_width="wrap_content"
                                android:layout_height="wrap_content"
                                android:background="@null"
                                android:clickable="false"
                                android:padding="5dip"
                                android:src="@drawable/ic_shopping_cart_black_24dp" />

                            <TextView
                                android:id="@+id/txtNoftify"
                                android:layout_width="wrap_content"
                                android:layout_height="wrap_content"
                                android:layout_alignRight="@id/cartButton"
                                android:layout_alignTop="@id/cartButton"
                                android:background="@drawable/notification_circle"
                                android:gravity="center"
                                android:textAlignment="center"
                                android:text="0"
                                android:textColor="#fff"
                                android:textSize="10sp" />
                                
                        </RelativeLayout>
                        
 Step 4. notification_circle (put it into drawable directory)
  
                    <?xml version="1.0" encoding="utf-8"?>
                    <shape android:dither="true" android:visible="true" android:shape="oval" android:useLevel="false"
                        xmlns:android="http://schemas.android.com/apk/res/android">
                        <gradient android:startColor="#009900"
                            android:endColor="#009900"
                            android:angle="270.0" />
                        <corners
                            android:radius="20dip" />
                        <size android:height="20dip"
                            android:width="20dip" />
                    </shape>


Step 5. In activity or fragment 

        
         private void makeFlyAnimation(ImageView targetView) {

                
                RelativeLayout destView = findViewById(R.id.cartRelative);

                new CircleAnimationUtil().attachActivity(this).setBorderColor(R.color.white).setBorderWidth(1).setTargetView(targetView).setCircleDuration(1000).setMoveDuration(800).setDestView(destView).setAnimationListener(new Animator.AnimatorListener() {
                    @Override
                    public void onAnimationStart(Animator animation) {

                    }

                    @Override
                    public void onAnimationEnd(Animator animation) {
                       /*
                       put your code here what to do after animation end
                       */
                    }

                    @Override
                    public void onAnimationCancel(Animator animation) {

                    }

                    @Override
                    public void onAnimationRepeat(Animator animation) {

                    }
                }).startAnimation();

            }
            
 Source : http://codezlab.com/add-to-cart-fly-animation/            

![](animation.gif)
